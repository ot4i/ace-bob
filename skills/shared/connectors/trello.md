# Trello

## Purpose
Connector-specific rules for Trello Request nodes.

## When to use
Use this document when the requested ACE flow includes a Trello Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Trello Request node

## Required node attributes
### Trello Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_trello.msgnode`
- `applicationConnectorType="trello"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Trello Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Trello Request nodes:

- `displayName="Retrieve actions"` `action="RETRIEVEALL"` `businessObject="Action"`
- `displayName="Retrieve action"` `action="RETRIEVE"` `businessObject="Action"`
- `displayName="Update action"` `action="UPDATEALL"` `businessObject="Action"`
- `displayName="Delete action"` `action="DELETEALL"` `businessObject="Action"`
- `displayName="Create board"` `action="CREATE"` `businessObject="Board"`
- `displayName="Retrieve boards"` `action="RETRIEVEALL"` `businessObject="Board"`
- `displayName="Retrieve board"` `action="RETRIEVE"` `businessObject="Board"`
- `displayName="Update board"` `action="UPDATEALL"` `businessObject="Board"`
- `displayName="Create card"` `action="CREATE"` `businessObject="Card"`
- `displayName="Retrieve cards"` `action="RETRIEVEALL"` `businessObject="Card"`
- `displayName="Retrieve card"` `action="RETRIEVE"` `businessObject="Card"`
- `displayName="Update card"` `action="UPDATEALL"` `businessObject="Card"`
- `displayName="Delete card"` `action="DELETEALL"` `businessObject="Card"`
- `displayName="Create checklist"` `action="CREATE"` `businessObject="Checklist"`
- `displayName="Retrieve checklists"` `action="RETRIEVEALL"` `businessObject="Checklist"`
- `displayName="Retrieve checklist"` `action="RETRIEVE"` `businessObject="Checklist"`
- `displayName="Update checklist"` `action="UPDATEALL"` `businessObject="Checklist"`
- `displayName="Delete checklist"` `action="DELETEALL"` `businessObject="Checklist"`
- `displayName="Create label"` `action="CREATE"` `businessObject="Label"`
- `displayName="Retrieve labels"` `action="RETRIEVEALL"` `businessObject="Label"`
- `displayName="Retrieve label"` `action="RETRIEVE"` `businessObject="Label"`
- `displayName="Update label"` `action="UPDATEALL"` `businessObject="Label"`
- `displayName="Delete label"` `action="DELETEALL"` `businessObject="Label"`
- `displayName="Create list"` `action="CREATE"` `businessObject="List"`
- `displayName="Retrieve lists"` `action="RETRIEVEALL"` `businessObject="List"`
- `displayName="Retrieve list"` `action="RETRIEVE"` `businessObject="List"`
- `displayName="Update list"` `action="UPDATEALL"` `businessObject="List"`
- `displayName="Create member"` `action="CREATE"` `businessObject="Member"`
- `displayName="Retrieve members"` `action="RETRIEVEALL"` `businessObject="Member"`
- `displayName="Retrieve member"` `action="RETRIEVE"` `businessObject="Member"`
- `displayName="Update member"` `action="UPDATEALL"` `businessObject="Member"`
- `displayName="Create organization"` `action="CREATE"` `businessObject="Organization"`
- `displayName="Retrieve organizations"` `action="RETRIEVEALL"` `businessObject="Organization"`
- `displayName="Retrieve organization"` `action="RETRIEVE"` `businessObject="Organization"`
- `displayName="Update organization"` `action="UPDATEALL"` `businessObject="Organization"`
- `displayName="Delete organization"` `action="DELETEALL"` `businessObject="Organization"`
- `displayName="Create attachment"` `action="CREATE"` `businessObject="Attachment"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="Attachment"`
- `displayName="Delete attachment"` `action="DELETEALL"` `businessObject="Attachment"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comment"`
- `displayName="Update comment"` `action="UPDATEALL"` `businessObject="Comment"`
- `displayName="Delete comment"` `action="DELETEALL"` `businessObject="Comment"`
- `displayName="Create check item"` `action="CREATE"` `businessObject="Checkitem"`
- `displayName="Retrieve check items"` `action="RETRIEVEALL"` `businessObject="Checkitem"`
- `displayName="Delete check item"` `action="DELETEALL"` `businessObject="Checkitem"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Trello1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Trello1" policyTemplate="online_v1_basic_oauth" policyType="trello" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
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
