# Coupa

## Purpose
Connector-specific rules for Coupa Request nodes.

## When to use
Use this document when the requested ACE flow includes a Coupa Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Coupa Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_coupa.msgnode`
- `applicationConnectorType="coupa"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Coupa Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Coupa Request nodes:

- `displayName="Create lookup value"` `action="CREATE"` `businessObject="lookup_values"`
- `displayName="Retrieve lookup value"` `action="RETRIEVEALL"` `businessObject="lookup_values"`
- `displayName="Retrieve lookup value by ID"` `action="RETRIEVE"` `businessObject="lookup_values"`
- `displayName="Update lookup value"` `action="UPDATEALL"` `businessObject="lookup_values"`
- `displayName="Create supplier"` `action="CREATE"` `businessObject="suppliers"`
- `displayName="Retrieve supplier"` `action="RETRIEVEALL"` `businessObject="suppliers"`
- `displayName="Retrieve supplier by ID"` `action="RETRIEVE"` `businessObject="suppliers"`
- `displayName="Update supplier"` `action="UPDATE"` `businessObject="suppliers"`
- `displayName="Create expense report"` `action="CREATE"` `businessObject="expense_reports"`
- `displayName="Retrieve expense report"` `action="RETRIEVEALL"` `businessObject="expense_reports"`
- `displayName="Retrieve expense report by ID"` `action="RETRIEVE"` `businessObject="expense_reports"`
- `displayName="Update expense report"` `action="UPDATE"` `businessObject="expense_reports"`
- `displayName="Retrieve purchase order"` `action="RETRIEVEALL"` `businessObject="purchase_orders"`
- `displayName="Retrieve purchase order by ID"` `action="RETRIEVE"` `businessObject="purchase_orders"`
- `displayName="Update purchase order"` `action="UPDATE"` `businessObject="purchase_orders"`
- `displayName="Retrieve inventory transaction"` `action="RETRIEVEALL"` `businessObject="inventory_transactions"`
- `displayName="Retrieve inventory transaction by ID"` `action="RETRIEVE"` `businessObject="inventory_transactions"`
- `displayName="Create invoice"` `action="CREATE"` `businessObject="invoices"`
- `displayName="Retrieve invoice"` `action="RETRIEVEALL"` `businessObject="invoices"`
- `displayName="Retrieve invoice by ID"` `action="RETRIEVE"` `businessObject="invoices"`
- `displayName="Update invoice"` `action="UPDATE"` `businessObject="invoices"`
- `displayName="Create exchange rate"` `action="CREATE"` `businessObject="exchange_rates"`
- `displayName="Retrieve exchange rate"` `action="RETRIEVEALL"` `businessObject="exchange_rates"`
- `displayName="Retrieve exchange rate by ID"` `action="RETRIEVE"` `businessObject="exchange_rates"`
- `displayName="Update exchange rate"` `action="UPDATE"` `businessObject="exchange_rates"`
- `displayName="Create remit to address"` `action="CREATE"` `businessObject="remit_to_addresses"`
- `displayName="Retrieve remit to address"` `action="RETRIEVEALL"` `businessObject="remit_to_addresses"`
- `displayName="Retrieve remit to address by ID"` `action="RETRIEVE"` `businessObject="remit_to_addresses"`
- `displayName="Update remit to address"` `action="UPDATEALL"` `businessObject="remit_to_addresses"`
- `displayName="Create address"` `action="CREATE"` `businessObject="addresses"`
- `displayName="Retrieve address"` `action="RETRIEVEALL"` `businessObject="addresses"`
- `displayName="Retrieve address by ID"` `action="RETRIEVE"` `businessObject="addresses"`
- `displayName="Update address"` `action="UPDATE"` `businessObject="addresses"`
- `displayName="Create user"` `action="CREATE"` `businessObject="users"`
- `displayName="Retrieve user"` `action="RETRIEVEALL"` `businessObject="users"`
- `displayName="Retrieve user by ID"` `action="RETRIEVE"` `businessObject="users"`
- `displayName="Update user"` `action="UPDATE"` `businessObject="users"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Coupa1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Coupa1" policyTemplate="online_v1_oauth2_credentials" policyType="coupa" shortDescription="" version="">
        <credentialName>CoupaCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_CREDENTIALS</authenticationMethod>
        <apiUrl/>
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
