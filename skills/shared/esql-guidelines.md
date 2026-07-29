# ACE ESQL Guidelines

## Purpose
This document defines ACE-focused guidance for creating and refining ESQL used by Compute nodes.

## When to use
Use this document when generating or reviewing `.esql` files for ACE Compute nodes.

## Performance and tree navigation
- Declare `REFERENCE` variables when navigating heavily nested logical trees to reduce repeated navigation cost.
- Avoid unnecessary full tree copying when a change is limited to a small part of the message tree.
- Avoid multiple consecutive Compute nodes where a simpler design would achieve the same result.
- Avoid using `CARDINALITY` inside loops when the value can be determined once outside the loop.
- Minimize expensive string manipulation where a simpler approach is available.
- Minimize the number of statements when doing so improves clarity and efficiency.

## Field existence checks
- Use `LASTMOVE` or `CARDINALITY` when checking whether a field exists.
- Prefer the most direct existence check that matches the tree navigation pattern being used.

## Tree construction
- Consider `CREATE ... PARSE` when it is more efficient than serializing and reparsing a copied logical tree.
- Be deliberate about Compute node copy behavior and avoid unnecessary message assembly duplication.

## Cross-domain transformation (XML → JSON)

**Never use a direct tree assignment to convert between message domains**, for example:

```esql
-- WRONG: copies XML tree structure verbatim, produces duplicate keys for repeated elements
SET OutputRoot.JSON.Data = InputRoot.XMLNSC.SomeElement;
```

### Step 1 — Analyse the XML structure before writing any ESQL

**Before writing a single line of ESQL**, examine the XML input and answer this question for every element at every level of nesting:

> "Can more than one of these elements appear as siblings under the same parent?"

If the answer is yes — even for a deeply nested element like `<Initial>` inside `<Invoice>` — that element **must** be mapped to a JSON array. There are no exceptions.

Build an explicit repeatability table before writing code:

| XML element | Can repeat? | JSON mapping |
|---|---|---|
| `SaleList/Invoice` | yes | JSON.Array |
| `Invoice/Initial` | yes | JSON.Array |
| `Invoice/Item` | yes | JSON.Array |
| `Item/Code` | yes | JSON.Array |
| `Invoice/Surname` | no | scalar |

Do not start writing ESQL until this table is complete.

### Step 2 — Initialise the output domain correctly

Use `CREATE LASTCHILD OF OutputRoot DOMAIN 'JSON'` followed by `CREATE FIELD OutputRoot.JSON.Data` to initialise the JSON output domain. **Do not use `SET OutputRoot.JSON.Data = NULL`** — that form does not correctly establish the JSON domain in ACE.

```esql
SET OutputRoot.Properties = InputRoot.Properties;
CREATE LASTCHILD OF OutputRoot DOMAIN 'JSON';
CREATE FIELD OutputRoot.JSON.Data;
```

### Step 3 — Declare JSON arrays explicitly before populating them

Every repeating element **must** be declared as a typed JSON array using `CREATE FIELD ... IDENTITY (JSON.Array)` before any elements are added to it. Do not rely on indexed `SET` alone to create arrays.

```esql
CREATE FIELD OutputRoot.JSON.Data.SaleList TYPE JSON.Object;
CREATE FIELD OutputRoot.JSON.Data.SaleList.Invoice IDENTITY (JSON.Array)Invoice;
```

### Step 4 — Iterate with REFERENCE + WHILE LASTMOVE, not FOR loops

Use `DECLARE ... REFERENCE TO element[1]` + `WHILE LASTMOVE(...) DO` + `MOVE ... NEXTSIBLING NAME '...'` to iterate repeating elements. **Do not use `FOR srcX AS path[] DO` loops** — that form does not correctly traverse sibling nodes in the XMLNSC domain.

For each object in an array, create it explicitly with `CREATE LASTCHILD ... TYPE JSON.Object` before assigning its fields.

```esql
DECLARE invoiceRef REFERENCE TO InputRoot.XMLNSC.SaleEnvelope.SaleList.Invoice[1];
DECLARE invoiceIndex INTEGER 1;
WHILE LASTMOVE(invoiceRef) DO
    CREATE LASTCHILD OF OutputRoot.JSON.Data.SaleList.Invoice TYPE JSON.Object;

    -- Read scalars with FIELDVALUE()
    SET OutputRoot.JSON.Data.SaleList.Invoice.Item[invoiceIndex].Surname = FIELDVALUE(invoiceRef.Surname);
    SET OutputRoot.JSON.Data.SaleList.Invoice.Item[invoiceIndex].Balance = FIELDVALUE(invoiceRef.Balance);

    -- Nested array: declare it, then iterate
    CREATE FIELD OutputRoot.JSON.Data.SaleList.Invoice.Item[invoiceIndex].Initial IDENTITY (JSON.Array)Initial;
    DECLARE initialIndex INTEGER 1;
    DECLARE initialRef REFERENCE TO invoiceRef.Initial[1];
    WHILE LASTMOVE(initialRef) DO
        SET OutputRoot.JSON.Data.SaleList.Invoice.Item[invoiceIndex].Initial.Item[initialIndex] = FIELDVALUE(initialRef);
        SET initialIndex = initialIndex + 1;
        MOVE initialRef NEXTSIBLING NAME 'Initial';
    END WHILE;

    SET invoiceIndex = invoiceIndex + 1;
    MOVE invoiceRef NEXTSIBLING NAME 'Invoice';
END WHILE;
```

### Step 5 — Always use FIELDVALUE() for scalar reads

When reading a scalar value from the XMLNSC tree, always wrap it in `FIELDVALUE()`. Using a bare field reference (e.g. `srcInvoice.Surname`) returns a logical tree node, not a string value, and will produce incorrect JSON output.

```esql
-- WRONG
SET OutputRoot.JSON.Data.Surname = invoiceRef.Surname;

-- CORRECT
SET OutputRoot.JSON.Data.Surname = FIELDVALUE(invoiceRef.Surname);
```

### Step 6 — Use DECLARE REFERENCE for navigation efficiency

Declare `REFERENCE` variables for deeply nested input paths to avoid repeated tree navigation:

```esql
DECLARE saleEnvelope REFERENCE TO InputRoot.XMLNSC.SaleEnvelope;
DECLARE saleList REFERENCE TO saleEnvelope.SaleList;
```

This rule applies whenever the source and target domains differ (XMLNSC→JSON, XMLNSC→JSONARRAY, etc.).

## Transformation fidelity
- Preserve the requested message domain and target structure exactly.
- Do not change an XML-to-JSON request into XML-to-XML or any other domain transformation.
- Do not invent new element names, field names, wrapper objects, or business semantics unless the user explicitly requests them.
- Do not add calculations, enrichment, default values, formatting changes, aggregation, or derived values unless the user explicitly requests them.
- If the user provides an expected output shape, example ESQL, or reference implementation, match that structure as closely as possible.
- For mapping tasks, prefer faithful structural mapping over a redesigned example transformation.

## ESQL file structure
Every `.esql` file for a Compute node must use this skeleton. The module name must match the name given to the Compute node in the `.msgflow` file. The file must be placed in the same Application project as the `.msgflow`.

```esql
CREATE COMPUTE MODULE <ModuleName>_Compute
	CREATE FUNCTION Main() RETURNS BOOLEAN
	BEGIN
		-- implementation here
		RETURN TRUE;
	END;
END MODULE;
```

The `.esql` filename must match the module name, e.g. `XMLToJSON_Compute.esql` for module `XMLToJSON_Compute`.

## REFERENCE vs FIELDVALUE vs direct assignment

Use the correct form depending on what you need:

| Intent | Correct form | Wrong form |
|---|---|---|
| Navigate to a subtree for repeated access | `DECLARE x REFERENCE TO path;` | Repeating the full path each time |
| Read a scalar string/number from XMLNSC | `FIELDVALUE(ref.Field)` | `ref.Field` (returns a tree node, not a value) |
| Copy a scalar from one domain to another | `SET out.Field = FIELDVALUE(in.Field)` | `SET out.Field = in.Field` |
| Move a reference to the next sibling | `MOVE ref NEXTSIBLING NAME 'X';` | n/a — no shorthand alternative |

Always use `FIELDVALUE()` when reading leaf values from an XMLNSC tree for output to a different domain (JSON, MRM, etc.).

## Flow design considerations
- Prefer clean flow design over wiring every failure terminal individually when a consistent catch strategy is more suitable.
- Consider whether a subflow or shared library is more appropriate when logic is repeated.

## Validity guardrails
- Do not invent ESQL built-in functions or statements.
- `CREATE OUTPUTROOT DOMAIN(...)` is not a valid ESQL statement — do not generate it.
- `SET OutputRoot.JSON.Data = NULL` does not correctly establish the JSON domain — use `CREATE LASTCHILD OF OutputRoot DOMAIN 'JSON'` + `CREATE FIELD OutputRoot.JSON.Data` instead.
- Do not invent JSON scalar type syntax such as `JSON.String`, `JSON.Number`, or `JSON.Boolean`.
- If a requested function or syntax is uncertain, use known ACE ESQL constructs rather than guessing.

## Known valid ACE ESQL constructs
- `FIELDVALUE(...)` is a valid ACE ESQL built-in and must not be replaced because it is described as unresolved.
- `LASTMOVE(...)` is a valid ACE ESQL built-in for reference navigation.
- `MOVE ref NEXTSIBLING NAME 'X';` is valid ACE ESQL syntax.
- `TYPE JSON.Object` is valid ACE ESQL syntax for explicit JSON object creation.
- `CREATE FIELD ... IDENTITY (JSON.Array)` is valid ACE ESQL syntax for explicit JSON array creation.
- Create JSON scalar values by assigning them with `SET outRef.Field = value` rather than inventing typed scalar nodes.
- Do not claim that these constructs are invalid unless they are being used in a way that contradicts the ACE guidance in this file.

## Related files
- [`skills/ace-esql/SKILL.md`](../ace-esql/SKILL.md)
- [`skills/shared/review-checklist.md`](review-checklist.md)
