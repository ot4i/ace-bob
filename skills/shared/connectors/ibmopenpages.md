# IBM OpenPages with Watson

## Purpose
Connector-specific rules for IBM OpenPages with Watson Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM OpenPages with Watson Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM OpenPages with Watson Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ibmopenpages.msgnode`
- `applicationConnectorType="ibmopenpages"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM OpenPages with Watson Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM OpenPages with Watson Request nodes:

- `displayName="Create business entity"` `action="CREATE"` `businessObject="SOXBusEntity"`
- `displayName="Update business entity"` `action="UPDATEALL"` `businessObject="SOXBusEntity"`
- `displayName="Delete business entity"` `action="DELETEALL"` `businessObject="SOXBusEntity"`
- `displayName="Update or create business entity"` `action="UPSERTWITHWHERE"` `businessObject="SOXBusEntity"`
- `displayName="Retrieve business entities"` `action="RETRIEVEALL"` `businessObject="SOXBusEntity"`
- `displayName="Retrieve business entity associations"` `action="RETRIEVEALL"` `businessObject="associationSOXBusEntity"`
- `displayName="Add associations to business entity"` `action="ADDASSOCIATIONS"` `businessObject="associationSOXBusEntity"`
- `displayName="Remove business entity associations"` `action="REMOVEASSOCIATIONS"` `businessObject="associationSOXBusEntity"`
- `displayName="Create process"` `action="CREATE"` `businessObject="SOXProcess"`
- `displayName="Update process"` `action="UPDATEALL"` `businessObject="SOXProcess"`
- `displayName="Delete process"` `action="DELETEALL"` `businessObject="SOXProcess"`
- `displayName="Update or create process"` `action="UPSERTWITHWHERE"` `businessObject="SOXProcess"`
- `displayName="Retrieve processes"` `action="RETRIEVEALL"` `businessObject="SOXProcess"`
- `displayName="Retrieve process associations"` `action="RETRIEVEALL"` `businessObject="associationSOXProcess"`
- `displayName="Add associations to process"` `action="ADDASSOCIATIONS"` `businessObject="associationSOXProcess"`
- `displayName="Remove process associations"` `action="REMOVEASSOCIATIONS"` `businessObject="associationSOXProcess"`
- `displayName="Create risk"` `action="CREATE"` `businessObject="SOXRisk"`
- `displayName="Update risk"` `action="UPDATEALL"` `businessObject="SOXRisk"`
- `displayName="Delete risk"` `action="DELETEALL"` `businessObject="SOXRisk"`
- `displayName="Update or create risk"` `action="UPSERTWITHWHERE"` `businessObject="SOXRisk"`
- `displayName="Retrieve risks"` `action="RETRIEVEALL"` `businessObject="SOXRisk"`
- `displayName="Retrieve risk associations"` `action="RETRIEVEALL"` `businessObject="associationSOXRisk"`
- `displayName="Add associations to risk"` `action="ADDASSOCIATIONS"` `businessObject="associationSOXRisk"`
- `displayName="Remove risk associations"` `action="REMOVEASSOCIATIONS"` `businessObject="associationSOXRisk"`
- `displayName="Create control"` `action="CREATE"` `businessObject="SOXControl"`
- `displayName="Update control"` `action="UPDATEALL"` `businessObject="SOXControl"`
- `displayName="Delete control"` `action="DELETEALL"` `businessObject="SOXControl"`
- `displayName="Update or create control"` `action="UPSERTWITHWHERE"` `businessObject="SOXControl"`
- `displayName="Retrieve controls"` `action="RETRIEVEALL"` `businessObject="SOXControl"`
- `displayName="Retrieve control associations"` `action="RETRIEVEALL"` `businessObject="associationSOXControl"`
- `displayName="Add associations to control"` `action="ADDASSOCIATIONS"` `businessObject="associationSOXControl"`
- `displayName="Remove control associations"` `action="REMOVEASSOCIATIONS"` `businessObject="associationSOXControl"`
- `displayName="Create file"` `action="CREATE"` `businessObject="SOXDocument"`
- `displayName="Update file"` `action="UPDATEALL"` `businessObject="SOXDocument"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="SOXDocument"`
- `displayName="Update or create file"` `action="UPSERTWITHWHERE"` `businessObject="SOXDocument"`
- `displayName="Retrieve files"` `action="RETRIEVEALL"` `businessObject="SOXDocument"`
- `displayName="Upload file"` `action="UPLOADFILE"` `businessObject="SOXDocument"`
- `displayName="Download file"` `action="DOWNLOADFILE"` `businessObject="SOXDocument"`
- `displayName="Retrieve file associations"` `action="RETRIEVEALL"` `businessObject="associationSOXDocument"`
- `displayName="Add associations to file"` `action="ADDASSOCIATIONS"` `businessObject="associationSOXDocument"`
- `displayName="Remove file associations"` `action="REMOVEASSOCIATIONS"` `businessObject="associationSOXDocument"`
- `displayName="Create issue"` `action="CREATE"` `businessObject="SOXIssue"`
- `displayName="Update issue"` `action="UPDATEALL"` `businessObject="SOXIssue"`
- `displayName="Delete issue"` `action="DELETEALL"` `businessObject="SOXIssue"`
- `displayName="Update or create issue"` `action="UPSERTWITHWHERE"` `businessObject="SOXIssue"`
- `displayName="Retrieve issues"` `action="RETRIEVEALL"` `businessObject="SOXIssue"`
- `displayName="Retrieve issue associations"` `action="RETRIEVEALL"` `businessObject="associationSOXIssue"`
- `displayName="Add associations to issue"` `action="ADDASSOCIATIONS"` `businessObject="associationSOXIssue"`
- `displayName="Remove issue associations"` `action="REMOVEASSOCIATIONS"` `businessObject="associationSOXIssue"`
- `displayName="Create action item"` `action="CREATE"` `businessObject="SOXTask"`
- `displayName="Update action item"` `action="UPDATEALL"` `businessObject="SOXTask"`
- `displayName="Delete action item"` `action="DELETEALL"` `businessObject="SOXTask"`
- `displayName="Update or create action item"` `action="UPSERTWITHWHERE"` `businessObject="SOXTask"`
- `displayName="Retrieve action items"` `action="RETRIEVEALL"` `businessObject="SOXTask"`
- `displayName="Retrieve action item associations"` `action="RETRIEVEALL"` `businessObject="associationSOXTask"`
- `displayName="Add associations to action item"` `action="ADDASSOCIATIONS"` `businessObject="associationSOXTask"`
- `displayName="Remove action item associations"` `action="REMOVEASSOCIATIONS"` `businessObject="associationSOXTask"`
- `displayName="Create user"` `action="CREATE"` `businessObject="user"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="user"`
- `displayName="Update user"` `action="UPDATEALL"` `businessObject="user"`
- `displayName="Update or create user"` `action="UPSERTWITHWHERE"` `businessObject="user"`
- `displayName="Reset password"` `action="CHANGEPASSWORD"` `businessObject="user"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Ibmopenpages1`.
- This connector uses `applicationType="cloud"` and `authenticationMethod="BASIC_BEARER"`. The policy includes an `<endpointUrl>` field for the OpenPages instance URL and an `<instanceId>` field for the unique instance name.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Ibmopenpages1" policyTemplate="cloud_v1_basic_bearer" policyType="ibmopenpages" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>cloud</applicationType>
        <authenticationMethod>BASIC_BEARER</authenticationMethod>
        <endpointUrl/>
        <instanceId/>
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
