# Front

## Purpose
Connector-specific rules for Front Request nodes.

## When to use
Use this document when the requested ACE flow includes a Front Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Front Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_front.msgnode`
- `applicationConnectorType="front"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Front Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Front Request nodes:

- `displayName="Retrieve all accounts"` `action="RETRIEVEWITHWHERE"` `businessObject="Accounts"`
- `displayName="Create account"` `action="CREATE"` `businessObject="Accounts"`
- `displayName="Update account"` `action="UPDATE"` `businessObject="Accounts"`
- `displayName="Delete account"` `action="DELETE"` `businessObject="Accounts"`
- `displayName="Retrieve account by ID"` `action="RETRIEVE"` `businessObject="Accounts"`
- `displayName="Retrieve account contacts"` `action="RETRIEVEWITHWHERE"` `businessObject="Accounts"`
- `displayName="Add contacts to account"` `action="CREATE"` `businessObject="Accounts"`
- `displayName="Delete contacts from account"` `action="DELETE"` `businessObject="Accounts"`
- `displayName="Retrieve all channels"` `action="RETRIEVEWITHWHERE"` `businessObject="Channels"`
- `displayName="Retrieve channel by ID"` `action="RETRIEVE"` `businessObject="Channels"`
- `displayName="Create channel"` `action="CREATE"` `businessObject="Channels"`
- `displayName="Update channel"` `action="UPDATE"` `businessObject="Channels"`
- `displayName="Retrieve account custom fields"` `action="RETRIEVEWITHWHERE"` `businessObject="Custom fields"`
- `displayName="Retrieve contact custom fields"` `action="RETRIEVEWITHWHERE"` `businessObject="Custom fields"`
- `displayName="Retrieve conversation custom fields"` `action="RETRIEVEWITHWHERE"` `businessObject="Custom fields"`
- `displayName="Retrieve inbox custom fields"` `action="RETRIEVEWITHWHERE"` `businessObject="Custom fields"`
- `displayName="Retrieve all inboxes"` `action="RETRIEVEWITHWHERE"` `businessObject="Inbox"`
- `displayName="Create inbox"` `action="CREATE"` `businessObject="Inbox"`
- `displayName="Retrieve inbox by ID"` `action="RETRIEVE"` `businessObject="Inbox"`
- `displayName="Retrieve inbox channels"` `action="RETRIEVE"` `businessObject="Inbox"`
- `displayName="Retrieve inbox conversations"` `action="RETRIEVEWITHWHERE"` `businessObject="Inbox"`
- `displayName="Retrieve all contacts"` `action="RETRIEVEWITHWHERE"` `businessObject="Contacts"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contacts"`
- `displayName="Retrieve contact by ID"` `action="RETRIEVE"` `businessObject="Contacts"`
- `displayName="Update contact"` `action="UPDATE"` `businessObject="Contacts"`
- `displayName="Delete contact"` `action="DELETE"` `businessObject="Contacts"`
- `displayName="Retrieve all conversations"` `action="RETRIEVEWITHWHERE"` `businessObject="Conversations"`
- `displayName="Create discussion conversation"` `action="CREATE"` `businessObject="Conversations"`
- `displayName="Search conversation"` `action="RETRIEVEWITHWHERE"` `businessObject="Conversations"`
- `displayName="Retrieve conversation by ID"` `action="RETRIEVE"` `businessObject="Conversations"`
- `displayName="Update conversation"` `action="UPDATE"` `businessObject="Conversations"`
- `displayName="Retrieve conversation inboxes"` `action="RETRIEVE"` `businessObject="Conversations"`
- `displayName="Retrieve comment by ID"` `action="RETRIEVE"` `businessObject="Comments"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comments"`
- `displayName="Create message"` `action="CREATE"` `businessObject="Messages"`
- `displayName="Create message reply"` `action="CREATE"` `businessObject="Messages"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Front1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Front1" policyTemplate="online_v1_basic_bearer" policyType="front" shortDescription="" version="">
        <credentialName>FrontCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_BEARER</authenticationMethod>
        <apiUrl>https://api2.frontapp.com</apiUrl>
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
