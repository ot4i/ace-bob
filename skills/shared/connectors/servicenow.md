# ServiceNow

## Purpose
Connector-specific rules for ServiceNow Request and ServiceNow Input nodes.

## When to use
Use this document when the requested ACE flow includes a ServiceNow Request node or ServiceNow Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- ServiceNow Request node
- ServiceNow Input node

## Required node attributes
### ServiceNow Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_servicenow.msgnode`
- `applicationConnectorType="servicenow"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### ServiceNow Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_servicenow.msgnode`
- `applicationConnectorType="servicenow"`

## Schema file requirements
For ServiceNow Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for ServiceNow Request nodes:

- `displayName="Create asset"` `action="CREATE"` `businessObject="Asset"`
- `displayName="Retrieve assets"` `action="RETRIEVEALL"` `businessObject="Asset"`
- `displayName="Retrieve asset"` `action="RETRIEVE"` `businessObject="Asset"`
- `displayName="Update asset"` `action="UPDATEALL"` `businessObject="Asset"`
- `displayName="Delete asset"` `action="DELETEALL"` `businessObject="Asset"`
- `displayName="Update or create asset"` `action="UPSERTWITHWHERE"` `businessObject="Asset"`
- `displayName="Create incident"` `action="CREATE"` `businessObject="Incident"`
- `displayName="Retrieve incidents"` `action="RETRIEVEALL"` `businessObject="Incident"`
- `displayName="Retrieve incident"` `action="RETRIEVE"` `businessObject="Incident"`
- `displayName="Update incident"` `action="UPDATEALL"` `businessObject="Incident"`
- `displayName="Delete incident"` `action="DELETEALL"` `businessObject="Incident"`
- `displayName="Update or create incident"` `action="UPSERTWITHWHERE"` `businessObject="Incident"`
- `displayName="Create problem"` `action="CREATE"` `businessObject="Problem"`
- `displayName="Retrieve problems"` `action="RETRIEVEALL"` `businessObject="Problem"`
- `displayName="Retrieve problem"` `action="RETRIEVE"` `businessObject="Problem"`
- `displayName="Update problem"` `action="UPDATEALL"` `businessObject="Problem"`
- `displayName="Delete problem"` `action="DELETEALL"` `businessObject="Problem"`
- `displayName="Update or create problem"` `action="UPSERTWITHWHERE"` `businessObject="Problem"`
- `displayName="Create department"` `action="CREATE"` `businessObject="Department"`
- `displayName="Retrieve departments"` `action="RETRIEVEALL"` `businessObject="Department"`
- `displayName="Retrieve department"` `action="RETRIEVE"` `businessObject="Department"`
- `displayName="Update department"` `action="UPDATEALL"` `businessObject="Department"`
- `displayName="Delete department"` `action="DELETEALL"` `businessObject="Department"`
- `displayName="Update or create department"` `action="UPSERTWITHWHERE"` `businessObject="Department"`
- `displayName="Create ticket"` `action="CREATE"` `businessObject="Ticket"`
- `displayName="Retrieve tickets"` `action="RETRIEVEALL"` `businessObject="Ticket"`
- `displayName="Retrieve ticket"` `action="RETRIEVE"` `businessObject="Ticket"`
- `displayName="Update ticket"` `action="UPDATEALL"` `businessObject="Ticket"`
- `displayName="Delete ticket"` `action="DELETEALL"` `businessObject="Ticket"`
- `displayName="Update or create ticket"` `action="UPSERTWITHWHERE"` `businessObject="Ticket"`
- `displayName="Create user"` `action="CREATE"` `businessObject="User"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve user"` `action="RETRIEVE"` `businessObject="User"`
- `displayName="Update user"` `action="UPDATEALL"` `businessObject="User"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="User"`
- `displayName="Update or create user"` `action="UPSERTWITHWHERE"` `businessObject="User"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comment"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="Comment"`
- `displayName="Retrieve comment"` `action="RETRIEVE"` `businessObject="Comment"`
- `displayName="Update or create comment"` `action="UPSERTWITHWHERE"` `businessObject="Comment"`
- `displayName="Create attachment"` `action="CREATE"` `businessObject="Attachment"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="Attachment"`
- `displayName="Retrieve attachment"` `action="RETRIEVE"` `businessObject="Attachment"`
- `displayName="Update or create attachment"` `action="UPSERTWITHWHERE"` `businessObject="Attachment"`
- `displayName="Create knowledge article"` `action="CREATE"` `businessObject="Knowledge"`
- `displayName="Retrieve knowledge articles"` `action="RETRIEVEALL"` `businessObject="Knowledge"`
- `displayName="Retrieve knowledge article"` `action="RETRIEVE"` `businessObject="Knowledge"`
- `displayName="Delete knowledge article"` `action="DELETEALL"` `businessObject="Knowledge"`
- `displayName="Update or create knowledge article"` `action="UPSERTWITHWHERE"` `businessObject="Knowledge"`
- `displayName="Download knowledge article attachment"` `action="DOWNLOADATTACHMENT"` `businessObject="Knowledge"`
- `displayName="Get additional knowledge metadata"` `action="GETMETADATA"` `businessObject="Knowledge"`

The following combinations are allowed for ServiceNow Input nodes:

- `displayName="New asset"` `action="CREATED"` `businessObject="Asset"`
- `displayName="Updated asset"` `action="UPDATED"` `businessObject="Asset"`
- `displayName="New incident"` `action="CREATED"` `businessObject="Incident"`
- `displayName="Updated incident"` `action="UPDATED"` `businessObject="Incident"`
- `displayName="New problem"` `action="CREATED"` `businessObject="Problem"`
- `displayName="Updated problem"` `action="UPDATED"` `businessObject="Problem"`
- `displayName="New department"` `action="CREATED"` `businessObject="Department"`
- `displayName="Updated department"` `action="UPDATED"` `businessObject="Department"`
- `displayName="New ticket"` `action="CREATED"` `businessObject="Ticket"`
- `displayName="Updated ticket"` `action="UPDATED"` `businessObject="Ticket"`
- `displayName="New user"` `action="CREATED"` `businessObject="User"`
- `displayName="Updated user"` `action="UPDATED"` `businessObject="User"`
- `displayName="New attachment"` `action="CREATED"` `businessObject="Attachment"`
- `displayName="New comment"` `action="CREATED"` `businessObject="Comment"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:ServiceNow1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="ServiceNow1" policyTemplate="online_v1_basic" policyType="servicenow" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
