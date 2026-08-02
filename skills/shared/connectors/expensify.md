# Expensify

## Purpose
Connector-specific rules for Expensify Request nodes.

## When to use
Use this document when the requested ACE flow includes an Expensify Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Expensify Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_expensify.msgnode`
- `applicationConnectorType="expensify"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Expensify Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Expensify Request nodes:

- `displayName="Create policy"` `action="CREATE"` `businessObject="Policies"`
- `displayName="Update policy"` `action="UPDATE"` `businessObject="Policies"`
- `displayName="Retrieve policies"` `action="RETRIEVE"` `businessObject="Policies"`
- `displayName="Retrieve policy information"` `action="RETRIEVE"` `businessObject="Policies"`
- `displayName="Create expense"` `action="CREATE"` `businessObject="Expenses"`
- `displayName="Create report"` `action="CREATE"` `businessObject="Reports"`
- `displayName="Export report"` `action="CUSTOM"` `businessObject="Reports"`
- `displayName="Download report"` `action="CUSTOM"` `businessObject="Reports"`
- `displayName="Update report status"` `action="UPDATE"` `businessObject="Reports"`
- `displayName="Update or create employees"` `action="CUSTOM"` `businessObject="Employees"`
- `displayName="Delete employees"` `action="DELETE"` `businessObject="Employees"`
- `displayName="Create expense rules"` `action="CREATE"` `businessObject="Expense rules"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Expensify1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Expensify1" policyTemplate="online_v1_basic" policyType="expensify" shortDescription="" version="">
        <credentialName>ExpensifyCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl>https://integrations.expensify.com/Integration-Server/ExpensifyIntegrations</apiUrl>
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
