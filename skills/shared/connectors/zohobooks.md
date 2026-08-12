# Zoho Books

## Purpose
Connector-specific rules for Zoho Books Request nodes.

## When to use
Use this document when the requested ACE flow includes a Zoho Books Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Zoho Books Request node

## Connector type
Zoho Books uses the `LoopbackNative` discovery protocol with an OpenAPI spec. Operations are expressed using `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Zoho Books Request nodes:

- `displayName="Create customer"` `action="create"` `businessObject="Customers"`
- `displayName="Retrieve customers"` `action="retrievewithwhere"` `businessObject="Customers"`
- `displayName="Update customer"` `action="update"` `businessObject="Customers"`
- `displayName="Retrieve customer by ID"` `action="retrieve"` `businessObject="Customers"`
- `displayName="Create invoice"` `action="create"` `businessObject="Invoices"`
- `displayName="Retrieve invoices"` `action="retrievewithwhere"` `businessObject="Invoices"`
- `displayName="Update invoice"` `action="update"` `businessObject="Invoices"`
- `displayName="Retrieve invoice by ID"` `action="retrieve"` `businessObject="Invoices"`
- `displayName="Delete invoice"` `action="delete"` `businessObject="Invoices"`
- `displayName="Email invoice"` `action="custom"` `businessObject="Invoices"`
- `displayName="Retrieve items"` `action="retrievewithwhere"` `businessObject="Items"`
- `displayName="Create item"` `action="create"` `businessObject="Items"`
- `displayName="Create account"` `action="create"` `businessObject="Chart of accounts"`
- `displayName="Retrieve chart of accounts"` `action="retrievewithwhere"` `businessObject="Chart of accounts"`
- `displayName="Create expense"` `action="create"` `businessObject="Expenses"`
- `displayName="Retrieve expenses"` `action="retrievewithwhere"` `businessObject="Expenses"`
- `displayName="Update expense"` `action="update"` `businessObject="Expenses"`
- `displayName="Retrieve expense by ID"` `action="retrieve"` `businessObject="Expenses"`
- `displayName="Create employee for an expense"` `action="create"` `businessObject="Expenses"`
- `displayName="Retrieve employees of an expense"` `action="retrievewithwhere"` `businessObject="Expenses"`
- `displayName="Create quote"` `action="create"` `businessObject="Quotes"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Zohobooks1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Zohobooks1" policyTemplate="" policyType="zohobooks" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <apiUrl>https://www.zohoapis.com/books/v3</apiUrl>
        <tokenUrl>https://accounts.zoho.com/oauth/v2</tokenUrl>
        <domainName/>
        <isTlsEnabled>false</isTlsEnabled>
        <endpointUrl/>
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
