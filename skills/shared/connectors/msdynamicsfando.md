# Dynamics 365 Finance and Supply Chain Management

## Purpose
Connector-specific rules for Dynamics 365 Finance and Supply Chain Management Request nodes.

## When to use
Use this document when the requested ACE flow includes a Dynamics 365 Finance and Supply Chain Management Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Dynamics 365 Finance and Supply Chain Management Request node

## Required node attributes
### Dynamics 365 Finance and Supply Chain Management Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msdynamicsfando.msgnode`
- `applicationConnectorType="msdynamicsfando"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Dynamics 365 Finance and Supply Chain Management Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Dynamics 365 Finance and Supply Chain Management Request nodes:

- `displayName="Create employee"` `action="CREATE"` `businessObject="Employee"`
- `displayName="Retrieve employees"` `action="RETRIEVEALL"` `businessObject="Employee"`
- `displayName="Retrieve employee"` `action="RETRIEVE"` `businessObject="Employee"`
- `displayName="Update employee"` `action="UPDATEALL"` `businessObject="Employee"`
- `displayName="Delete employee"` `action="DELETEALL"` `businessObject="Employee"`
- `displayName="Create vendor"` `action="CREATE"` `businessObject="Vendor"`
- `displayName="Retrieve vendors"` `action="RETRIEVEALL"` `businessObject="Vendor"`
- `displayName="Retrieve vendor"` `action="RETRIEVE"` `businessObject="Vendor"`
- `displayName="Update vendor"` `action="UPDATEALL"` `businessObject="Vendor"`
- `displayName="Delete vendor"` `action="DELETEALL"` `businessObject="Vendor"`
- `displayName="Create project"` `action="CREATE"` `businessObject="Project"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Project"`
- `displayName="Retrieve project"` `action="RETRIEVE"` `businessObject="Project"`
- `displayName="Update project"` `action="UPDATEALL"` `businessObject="Project"`
- `displayName="Delete project"` `action="DELETEALL"` `businessObject="Project"`
- `displayName="Create operation"` `action="CREATE"` `businessObject="Operation"`
- `displayName="Retrieve operations"` `action="RETRIEVEALL"` `businessObject="Operation"`
- `displayName="Retrieve operation"` `action="RETRIEVE"` `businessObject="Operation"`
- `displayName="Update operation"` `action="UPDATEALL"` `businessObject="Operation"`
- `displayName="Delete operation"` `action="DELETEALL"` `businessObject="Operation"`
- `displayName="Create prospect"` `action="CREATE"` `businessObject="Prospect"`
- `displayName="Retrieve prospects"` `action="RETRIEVEALL"` `businessObject="Prospect"`
- `displayName="Retrieve prospect"` `action="RETRIEVE"` `businessObject="Prospect"`
- `displayName="Delete prospect"` `action="DELETEALL"` `businessObject="Prospect"`
- `displayName="Create user group"` `action="CREATE"` `businessObject="UserGroup"`
- `displayName="Retrieve user groups"` `action="RETRIEVEALL"` `businessObject="UserGroup"`
- `displayName="Retrieve user group"` `action="RETRIEVE"` `businessObject="UserGroup"`
- `displayName="Update user group"` `action="UPDATEALL"` `businessObject="UserGroup"`
- `displayName="Delete user group"` `action="DELETEALL"` `businessObject="UserGroup"`
- `displayName="Create applicant"` `action="CREATE"` `businessObject="Applicant"`
- `displayName="Retrieve applicants"` `action="RETRIEVEALL"` `businessObject="Applicant"`
- `displayName="Retrieve applicant"` `action="RETRIEVE"` `businessObject="Applicant"`
- `displayName="Update applicant"` `action="UPDATEALL"` `businessObject="Applicant"`
- `displayName="Delete applicant"` `action="DELETEALL"` `businessObject="Applicant"`
- `displayName="Create sales agreement"` `action="CREATE"` `businessObject="SalesAgreement"`
- `displayName="Retrieve sales agreements"` `action="RETRIEVEALL"` `businessObject="SalesAgreement"`
- `displayName="Retrieve sales agreement"` `action="RETRIEVE"` `businessObject="SalesAgreement"`
- `displayName="Delete sales agreement"` `action="DELETEALL"` `businessObject="SalesAgreement"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSDynamicsFandO1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSDynamicsFandO1" policyTemplate="online_v1_oauth2_credentials" policyType="msdynamicsfando" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_CREDENTIALS</authenticationMethod>
        <endpointUrl/>
        <tenantId/>
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
