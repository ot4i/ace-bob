# SAP S/4HANA

## Purpose
Connector-specific rules for SAP S/4HANA Request nodes.

## When to use
Use this document when the requested ACE flow includes a SAP S/4HANA Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- SAP S/4HANA Request node

## Connector type
SAP S/4HANA is a **dynamic (runtime-discovery)** connector. It does not use the legacy `xmi:type` / `applicationConnectorType` attributes, and it has no static OpenAPI spec. The connector is implemented in [`appconnect-connector-saps4hana`](../appconnect-connector-saps4hana/) and dynamically discovers entities and generates operations at runtime by fetching and parsing EDMX metadata from the configured SAP OData V2 services.

## Schema file requirements
For SAP S/4HANA Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
Operations are **dynamically generated** for each OData entity discovered from the configured services. The connector generates four standard CRUD operations per entity using the following action prefixes (defined in [`lib/utils/constants.js`](../appconnect-connector-saps4hana/lib/utils/constants.js)):

| Operation type | Action prefix | ACE operation type |
|---|---|---|
| Create entity | `Create_` | `create` |
| Retrieve entities (with filtering and pagination) | `ReadAll_` | `retrievewithwhere` |
| Retrieve entity by key | `Get_` | `retrieve` |
| Update entity | `Update_` | `update` |
| Delete entity | `Delete_` | `delete` |

For example, for an entity named `A_SalesOrder` discovered from the `API_SALES_ORDER_SRV` service, the connector generates:
- `Create_A_SalesOrder` — `action="create"`
- `ReadAll_A_SalesOrder` — `action="retrievewithwhere"`
- `Get_A_SalesOrder` — `action="retrieve"`
- `Update_A_SalesOrder` — `action="update"`
- `Delete_A_SalesOrder` — `action="delete"`

Not all five operations are generated for every entity; the set depends on the capabilities declared in the OData metadata for that entity.

### Pagination
Retrieve operations use skip-limit pagination with parameters `skipRecords` (maps to OData `$skip`) and `limitRecords` (maps to OData `$top`). Default page size is 50.

### Filtering
Retrieve operations support OData filtering:
- Numeric, date, and boolean properties: `eq`, `gt`, `lt`, `gte`, `lte`
- String properties: `eq`, `contains` (OData `substringof`), `startswith`, `endswith`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:SapS4hana1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="SapS4hana1" policyTemplate="online_v1_basic" policyType="saps4hana" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <odataService/>
        <proxyId/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
