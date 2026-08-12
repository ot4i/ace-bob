# Kronos

## Purpose
Connector-specific rules for Kronos (UKG) Request nodes.

## When to use
Use this document when the requested ACE flow includes a Kronos Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Kronos Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_kronos.msgnode`
- `applicationConnectorType="kronos"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Kronos Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Kronos Request nodes:

- `displayName="Retrieve attendance records"` `action="RETRIEVEALL"` `businessObject="attendance"`
- `displayName="Reset attendance balance (deprecated)"` `action="UPDATEALL"` `businessObject="attendance"`
- `displayName="Reset attendance balance"` `action="RESETBALANCES"` `businessObject="attendance"`
- `displayName="Retrieve attendance balance types"` `action="RETRIEVEALL"` `businessObject="attendanceBalanceType"`
- `displayName="Retrieve employees"` `action="RETRIEVEALL"` `businessObject="employee"`
- `displayName="Retrieve employee schedules"` `action="GETEMPLOYEESCHEDULE"` `businessObject="employeeSchedule"`
- `displayName="Retrieve employee employment details"` `action="GETEMPLOYEEEXTENSION"` `businessObject="extension"`
- `displayName="Retrieve employee job preferences"` `action="RETRIEVEALL"` `businessObject="jobPreference"`
- `displayName="Retrieve employee leave records"` `action="RETRIEVEALL"` `businessObject="leave"`
- `displayName="Create person"` `action="CREATE"` `businessObject="person"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Kronos1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Kronos1" policyTemplate="online_v1_oauth2_password" policyType="kronos" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_PASSWORD</authenticationMethod>
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
