# Microsoft Exchange

## Purpose
Connector-specific rules for Microsoft Exchange Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Exchange Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Exchange Request node

## Required node attributes
### Microsoft Exchange Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msexchange.msgnode`
- `applicationConnectorType="msexchange"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft Exchange Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Exchange Request nodes:

- `displayName="Create attachment"` `action="CREATE"` `businessObject="Attachment"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="Attachment"`
- `displayName="Retrieve attachment"` `action="RETRIEVE"` `businessObject="Attachment"`
- `displayName="Delete attachment"` `action="DELETEALL"` `businessObject="Attachment"`
- `displayName="Create calendar event"` `action="CREATE"` `businessObject="CalendarEvent"`
- `displayName="Retrieve calendar events"` `action="RETRIEVEALL"` `businessObject="CalendarEvent"`
- `displayName="Retrieve calendar event"` `action="RETRIEVE"` `businessObject="CalendarEvent"`
- `displayName="Update calendar event"` `action="UPDATEALL"` `businessObject="CalendarEvent"`
- `displayName="Delete calendar event"` `action="DELETEALL"` `businessObject="CalendarEvent"`
- `displayName="Create calendar group"` `action="CREATE"` `businessObject="CalendarGroup"`
- `displayName="Retrieve calendar groups"` `action="RETRIEVEALL"` `businessObject="CalendarGroup"`
- `displayName="Retrieve calendar group"` `action="RETRIEVE"` `businessObject="CalendarGroup"`
- `displayName="Update calendar group"` `action="UPDATEALL"` `businessObject="CalendarGroup"`
- `displayName="Delete calendar group"` `action="DELETEALL"` `businessObject="CalendarGroup"`
- `displayName="Create calendar"` `action="CREATE"` `businessObject="Calendar"`
- `displayName="Retrieve calendars"` `action="RETRIEVEALL"` `businessObject="Calendar"`
- `displayName="Retrieve calendar"` `action="RETRIEVE"` `businessObject="Calendar"`
- `displayName="Update calendar"` `action="UPDATEALL"` `businessObject="Calendar"`
- `displayName="Delete calendar"` `action="DELETEALL"` `businessObject="Calendar"`
- `displayName="Create contact folder"` `action="CREATE"` `businessObject="ContactFolder"`
- `displayName="Retrieve contact folders"` `action="RETRIEVEALL"` `businessObject="ContactFolder"`
- `displayName="Retrieve contact folder"` `action="RETRIEVE"` `businessObject="ContactFolder"`
- `displayName="Update contact folder"` `action="UPDATEALL"` `businessObject="ContactFolder"`
- `displayName="Delete contact folder"` `action="DELETEALL"` `businessObject="ContactFolder"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contact"`
- `displayName="Retrieve contact"` `action="RETRIEVE"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contact"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contact"`
- `displayName="Create conversation"` `action="CREATE"` `businessObject="Conversation"`
- `displayName="Retrieve conversations"` `action="RETRIEVEALL"` `businessObject="Conversation"`
- `displayName="Retrieve conversation"` `action="RETRIEVE"` `businessObject="Conversation"`
- `displayName="Update conversation"` `action="UPDATEALL"` `businessObject="Conversation"`
- `displayName="Create email"` `action="CREATE"` `businessObject="Email"`
- `displayName="Retrieve emails"` `action="RETRIEVEALL"` `businessObject="Email"`
- `displayName="Retrieve email"` `action="RETRIEVE"` `businessObject="Email"`
- `displayName="Update email"` `action="UPDATEALL"` `businessObject="Email"`
- `displayName="Delete email"` `action="DELETEALL"` `businessObject="Email"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Retrieve group"` `action="RETRIEVE"` `businessObject="Group"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="Group"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="Group"`
- `displayName="Create mail folder"` `action="CREATE"` `businessObject="MailFolder"`
- `displayName="Retrieve mail folders"` `action="RETRIEVEALL"` `businessObject="MailFolder"`
- `displayName="Retrieve mail folder"` `action="RETRIEVE"` `businessObject="MailFolder"`
- `displayName="Update mail folder"` `action="UPDATEALL"` `businessObject="MailFolder"`
- `displayName="Delete mail folder"` `action="DELETEALL"` `businessObject="MailFolder"`
- `displayName="Retrieve organizations"` `action="RETRIEVEALL"` `businessObject="Organization"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSExchange1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSExchange1" policyTemplate="admin_v1_basic_oauth" policyType="msexchange" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>admin</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
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
