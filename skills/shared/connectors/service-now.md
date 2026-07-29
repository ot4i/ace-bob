# ServiceNow

## Purpose
Connector-specific rules for ServiceNow Request and Input nodes.

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

- `displayName="Create incident"` `action="CREATE"` `businessObject="incident"`
- `displayName="Update incident"` `action="UPDATE"` `businessObject="incident"`
- `displayName="Update incidents"` `action="UPDATEALL"` `businessObject="incident"`
- `displayName="Retrieve incident"` `action="RETRIEVE"` `businessObject="incident"`
- `displayName="Retrieve incidents"` `action="RETRIEVEALL"` `businessObject="incident"`
- `displayName="Delete incidents"` `action="DELETEALL"` `businessObject="incident"`
- `displayName="Update or create incident"` `action="UPSERTWITHWHERE"` `businessObject="incident"`
- `displayName="New incident"` `action="CREATED"` `businessObject="incident"`
- `displayName="Updated incident"` `action="UPDATED"` `businessObject="incident"`
- `displayName="Create asset"` `action="CREATE"` `businessObject="alm_asset"`
- `displayName="Update asset"` `action="UPDATE"` `businessObject="alm_asset"`
- `displayName="Update assets"` `action="UPDATEALL"` `businessObject="alm_asset"`
- `displayName="Retrieve asset"` `action="RETRIEVE"` `businessObject="alm_asset"`
- `displayName="Retrieve assets"` `action="RETRIEVEALL"` `businessObject="alm_asset"`
- `displayName="Delete assets"` `action="DELETEALL"` `businessObject="alm_asset"`
- `displayName="Update or create asset"` `action="UPSERTWITHWHERE"` `businessObject="alm_asset"`
- `displayName="New asset"` `action="CREATED"` `businessObject="alm_asset"`
- `displayName="Updated asset"` `action="UPDATED"` `businessObject="alm_asset"`
- `displayName="Create department"` `action="CREATE"` `businessObject="cmn_department"`
- `displayName="Update department"` `action="UPDATE"` `businessObject="cmn_department"`
- `displayName="Update departments"` `action="UPDATEALL"` `businessObject="cmn_department"`
- `displayName="Retrieve department"` `action="RETRIEVE"` `businessObject="cmn_department"`
- `displayName="Retrieve departments"` `action="RETRIEVEALL"` `businessObject="cmn_department"`
- `displayName="Delete departments"` `action="DELETEALL"` `businessObject="cmn_department"`
- `displayName="Update or create department"` `action="UPSERTWITHWHERE"` `businessObject="cmn_department"`
- `displayName="New department"` `action="CREATED"` `businessObject="cmn_department"`
- `displayName="Updated department"` `action="UPDATED"` `businessObject="cmn_department"`
- `displayName="Create problem"` `action="CREATE"` `businessObject="problem"`
- `displayName="Update problem"` `action="UPDATE"` `businessObject="problem"`
- `displayName="Update problems"` `action="UPDATEALL"` `businessObject="problem"`
- `displayName="Retrieve problem"` `action="RETRIEVE"` `businessObject="problem"`
- `displayName="Retrieve problems"` `action="RETRIEVEALL"` `businessObject="problem"`
- `displayName="Delete problems"` `action="DELETEALL"` `businessObject="problem"`
- `displayName="Update or create problem"` `action="UPSERTWITHWHERE"` `businessObject="problem"`
- `displayName="New problem"` `action="CREATED"` `businessObject="problem"`
- `displayName="Updated problem"` `action="UPDATED"` `businessObject="problem"`
- `displayName="Create ticket"` `action="CREATE"` `businessObject="ticket"`
- `displayName="Update ticket"` `action="UPDATE"` `businessObject="ticket"`
- `displayName="Update tickets"` `action="UPDATEALL"` `businessObject="ticket"`
- `displayName="Retrieve ticket"` `action="RETRIEVE"` `businessObject="ticket"`
- `displayName="Retrieve tickets"` `action="RETRIEVEALL"` `businessObject="ticket"`
- `displayName="Delete tickets"` `action="DELETEALL"` `businessObject="ticket"`
- `displayName="Update or create ticket"` `action="UPSERTWITHWHERE"` `businessObject="ticket"`
- `displayName="New ticket"` `action="CREATED"` `businessObject="ticket"`
- `displayName="Updated ticket"` `action="UPDATED"` `businessObject="ticket"`
- `displayName="Create system user"` `action="CREATE"` `businessObject="sys_user"`
- `displayName="Update system user"` `action="UPDATE"` `businessObject="sys_user"`
- `displayName="Updates system users"` `action="UPDATEALL"` `businessObject="sys_user"`
- `displayName="Retrieve system user"` `action="RETRIEVE"` `businessObject="sys_user"`
- `displayName="Retrieve system users"` `action="RETRIEVEALL"` `businessObject="sys_user"`
- `displayName="Delete system users"` `action="DELETEALL"` `businessObject="sys_user"`
- `displayName="Update or create system user"` `action="UPSERTWITHWHERE"` `businessObject="sys_user"`
- `displayName="New system user"` `action="CREATED"` `businessObject="sys_user"`
- `displayName="Updated system user"` `action="UPDATED"` `businessObject="sys_user"`
- `displayName="Create attachment"` `action="CREATE"` `businessObject="sys_attachment"`
- `displayName="Update attachment"` `action="UPDATE"` `businessObject="sys_attachment"`
- `displayName="Retrieve attachment"` `action="RETRIEVE"` `businessObject="sys_attachment"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="sys_attachment"`
- `displayName="Update or create attachment"` `action="UPSERTWITHWHERE"` `businessObject="sys_attachment"`
- `displayName="Download File Attachment Content"` `action="DOWNLOADATTACHMENT"` `businessObject="sys_attachment"`
- `displayName="New attachment"` `action="CREATED"` `businessObject="sys_attachment"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="sys_journal_field"`
- `displayName="Update comment"` `action="UPDATE"` `businessObject="sys_journal_field"`
- `displayName="Update comments"` `action="UPDATEALL"` `businessObject="sys_journal_field"`
- `displayName="Retrieve comment"` `action="RETRIEVE"` `businessObject="sys_journal_field"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="sys_journal_field"`
- `displayName="Update or create comment"` `action="UPSERTWITHWHERE"` `businessObject="sys_journal_field"`
- `displayName="New comment"` `action="CREATED"` `businessObject="sys_journal_field"`
- `displayName="Create knowledge"` `action="CREATE"` `businessObject="kb_knowledge"`
- `displayName="Update knowledge"` `action="UPDATE"` `businessObject="kb_knowledge"`
- `displayName="Update knowledge"` `action="UPDATEALL"` `businessObject="kb_knowledge"`
- `displayName="Retrieve knowledge"` `action="RETRIEVEALL"` `businessObject="kb_knowledge"`
- `displayName="Update or create knowledge"` `action="UPSERTWITHWHERE"` `businessObject="kb_knowledge"`
- `displayName="Delete knowledge"` `action="DELETEALL"` `businessObject="kb_knowledge"`
- `displayName="Download knowledge article attachment"` `action="DOWNLOADARTICLEATTACHMENT"` `businessObject="kb_knowledge_article"`
- `displayName="Get additional knowledge metadata"` `action="GETKNOWLEDGEARTICLEDETAILS"` `businessObject="kb_knowledge_article"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:ServiceNow1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Example" policyTemplate="online_v1_basic" policyType="servicenow" shortDescription="" version="">
     <credentialName>ServiceNowCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <endpointUrl>YourEndpointURL</endpointUrl>
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
