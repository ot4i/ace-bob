# Factorial HR

## Purpose
Connector-specific rules for Factorial HR Request nodes.

## When to use
Use this document when the requested ACE flow includes a Factorial HR Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Factorial HR Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_factorialhr.msgnode`
- `applicationConnectorType="factorialhr"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Factorial HR Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Factorial HR Request nodes:

- `displayName="Create employee"` `action="CREATE"` `businessObject="Employees"`
- `displayName="Retrieve employees"` `action="RETRIEVEWITHWHERE"` `businessObject="Employees"`
- `displayName="Retrieve employee by ID"` `action="RETRIEVE"` `businessObject="Employees"`
- `displayName="Update employee"` `action="UPDATE"` `businessObject="Employees"`
- `displayName="Create employee clock in"` `action="CREATE"` `businessObject="Attendances"`
- `displayName="Create employee clock out"` `action="CREATE"` `businessObject="Attendances"`
- `displayName="Retrieve shifts"` `action="RETRIEVEWITHWHERE"` `businessObject="Attendances"`
- `displayName="Create absence"` `action="CREATE"` `businessObject="Absences"`
- `displayName="Retrieve absence details"` `action="RETRIEVEWITHWHERE"` `businessObject="Absences"`
- `displayName="Retrieve absence type details"` `action="RETRIEVEWITHWHERE"` `businessObject="Absence types"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Tasks"`
- `displayName="Retrieve tasks"` `action="RETRIEVEWITHWHERE"` `businessObject="Tasks"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:FactorialHR1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="FactorialHR1" policyTemplate="online_v1_basic_oauth" policyType="factorialhr" shortDescription="" version="">
        <credentialName>FactorialHRCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <apiUrl>https://api.factorialhr.com</apiUrl>
        <isTlsEnabled>false</isTlsEnabled>
        <endpointUrl/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
