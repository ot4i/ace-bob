# BambooHR

## Purpose
Connector-specific rules for BambooHR Request nodes.

## When to use
Use this document when the requested ACE flow includes a BambooHR Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- BambooHR Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_bamboohr.msgnode`
- `applicationConnectorType="bamboohr"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For BambooHR Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for BambooHR Request nodes:

- `displayName="Create employee"` `action="CREATE"` `businessObject="employees"`
- `displayName="Retrieve employees"` `action="RETRIEVEALL"` `businessObject="employees"`
- `displayName="Update employee"` `action="UPDATEALL"` `businessObject="employees"`
- `displayName="Update or create employee"` `action="UPSERTWITHWHERE"` `businessObject="employees"`
- `displayName="Create employee dependent"` `action="CREATE"` `businessObject="dependents"`
- `displayName="Retrieve employee dependents"` `action="RETRIEVEALL"` `businessObject="dependents"`
- `displayName="Update employee dependent"` `action="UPDATEALL"` `businessObject="dependents"`
- `displayName="Update or create employee dependent"` `action="UPSERTWITHWHERE"` `businessObject="dependents"`
- `displayName="Retrieve benefit deduction types"` `action="RETRIEVEALL"` `businessObject="benefits"`
- `displayName="Retrieve employee file by ID"` `action="RETRIEVEALL"` `businessObject="employeefiles"`
- `displayName="Download employee file content"` `action="DOWNLOADFILE"` `businessObject="employeefiles"`
- `displayName="Update employee file"` `action="UPDATEALL"` `businessObject="employeefiles"`
- `displayName="Delete employee file"` `action="DELETEALL"` `businessObject="employeefiles"`
- `displayName="Create employee report"` `action="CREATEREPORT"` `businessObject="reports"`
- `displayName="Create time tracking record"` `action="CREATE"` `businessObject="timetracking"`
- `displayName="Retrieve time tracking record by ID"` `action="RETRIEVEALL"` `businessObject="timetracking"`
- `displayName="Retrieve list field details by name"` `action="RETRIEVEALL"` `businessObject="metalist"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:BambooHR1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="BambooHR1" policyTemplate="online_v1_basic_api_key" policyType="bamboohr" shortDescription="" version="">
     <credentialName>BambooHRCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_API_KEY</authenticationMethod>
     <subdomain/>
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
