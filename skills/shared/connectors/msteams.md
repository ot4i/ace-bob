# Microsoft Teams

## Purpose
Connector-specific rules for Microsoft Teams Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Teams Request node or a Microsoft Teams Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Teams Request node
- Microsoft Teams Input node

## Required node attributes
### Microsoft Teams Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msteams.msgnode`
- `applicationConnectorType="msteams"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Microsoft Teams Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_msteams.msgnode`
- `applicationConnectorType="msteams"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft Teams Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

For Microsoft Teams Input nodes:
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Teams Request nodes:

- `displayName="Retrieve teams"` `action="RETRIEVEALL"` `businessObject="Team"`
- `displayName="Retrieve team"` `action="RETRIEVE"` `businessObject="Team"`
- `displayName="Update team"` `action="UPDATEALL"` `businessObject="Team"`
- `displayName="Create channel"` `action="CREATE"` `businessObject="Channel"`
- `displayName="Retrieve channels"` `action="RETRIEVEALL"` `businessObject="Channel"`
- `displayName="Retrieve channel"` `action="RETRIEVE"` `businessObject="Channel"`
- `displayName="Update channel"` `action="UPDATEALL"` `businessObject="Channel"`
- `displayName="Delete channel"` `action="DELETEALL"` `businessObject="Channel"`
- `displayName="Create message reply"` `action="CREATE"` `businessObject="MessageReply"`
- `displayName="Retrieve message replies"` `action="RETRIEVEALL"` `businessObject="MessageReply"`
- `displayName="Retrieve message reply"` `action="RETRIEVE"` `businessObject="MessageReply"`
- `displayName="Create message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Retrieve message"` `action="RETRIEVE"` `businessObject="Message"`
- `displayName="Retrieve chats"` `action="RETRIEVEALL"` `businessObject="Chat"`
- `displayName="Retrieve chat"` `action="RETRIEVE"` `businessObject="Chat"`
- `displayName="Create chat message"` `action="CREATE"` `businessObject="ChatMessage"`
- `displayName="Retrieve chat messages"` `action="RETRIEVEALL"` `businessObject="ChatMessage"`
- `displayName="Retrieve chat message"` `action="RETRIEVE"` `businessObject="ChatMessage"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Retrieve group"` `action="RETRIEVE"` `businessObject="Group"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="Group"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="Group"`
- `displayName="Retrieve members"` `action="RETRIEVEALL"` `businessObject="Member"`
- `displayName="Delete member"` `action="DELETEALL"` `businessObject="Member"`
- `displayName="Retrieve owners"` `action="RETRIEVEALL"` `businessObject="Owner"`
- `displayName="Delete owner"` `action="DELETEALL"` `businessObject="Owner"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Create event"` `action="CREATE"` `businessObject="Event"`
- `displayName="Retrieve events"` `action="RETRIEVEALL"` `businessObject="Event"`
- `displayName="Retrieve event"` `action="RETRIEVE"` `businessObject="Event"`
- `displayName="Update event"` `action="UPDATEALL"` `businessObject="Event"`
- `displayName="Delete event"` `action="DELETEALL"` `businessObject="Event"`
- `displayName="Create online meeting"` `action="CREATE"` `businessObject="OnlineMeeting"`
- `displayName="Retrieve online meetings"` `action="RETRIEVEALL"` `businessObject="OnlineMeeting"`
- `displayName="Retrieve online meeting"` `action="RETRIEVE"` `businessObject="OnlineMeeting"`
- `displayName="Update online meeting"` `action="UPDATEALL"` `businessObject="OnlineMeeting"`
- `displayName="Delete online meeting"` `action="DELETEALL"` `businessObject="OnlineMeeting"`
- `displayName="Retrieve call recordings"` `action="RETRIEVEALL"` `businessObject="CallRecording"`
- `displayName="Retrieve call transcripts"` `action="RETRIEVEALL"` `businessObject="CallTranscript"`

The following combinations are allowed for Microsoft Teams Input nodes:

- `displayName="New message"` `action="CREATED"` `businessObject="Message"`
- `displayName="Updated message"` `action="UPDATED"` `businessObject="Message"`
- `displayName="Deleted message"` `action="DELETED"` `businessObject="Message"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSTeams1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSTeams1" policyTemplate="online_v1_basic_oauth" policyType="msteams" shortDescription="" version="">
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
