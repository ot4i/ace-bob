# Gmail

## Purpose
Connector-specific rules for Gmail Request and Gmail Input nodes.

## When to use
Use this document when the requested ACE flow includes a Gmail Request node or Gmail Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Gmail Request node
- Gmail Input node

## Required node attributes
### Gmail Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_gmail.msgnode`
- `applicationConnectorType="gmail"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Gmail Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_gmail.msgnode`
- `applicationConnectorType="gmail"`

## Schema file requirements
For Gmail Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Gmail Request nodes:

- `displayName="Send email"` `action="CREATE"` `businessObject="mail"`
- `displayName="Retrieve emails"` `action="RETRIEVEALL"` `businessObject="mail"`
- `displayName="Update email labels"` `action="UPDATEALL"` `businessObject="mail"`
- `displayName="Delete email"` `action="DELETEALL"` `businessObject="mail"`
- `displayName="List drafts"` `action="RETRIEVEALL"` `businessObject="Draft"`
- `displayName="Create draft"` `action="CREATE"` `businessObject="Draft"`
- `displayName="Retrieve draft"` `action="RETRIEVE"` `businessObject="Draft"`
- `displayName="Update draft"` `action="UPDATEALL"` `businessObject="Draft"`
- `displayName="Delete draft"` `action="DELETEALL"` `businessObject="Draft"`
- `displayName="Send draft"` `action="SENDDRAFT"` `businessObject="Draft"`
- `displayName="List messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Send message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve message"` `action="RETRIEVE"` `businessObject="Message"`
- `displayName="Delete message"` `action="DELETEALL"` `businessObject="Message"`
- `displayName="Modify message"` `action="UPDATEALL"` `businessObject="Message"`
- `displayName="Insert message"` `action="INSERTMESSAGE"` `businessObject="Message"`
- `displayName="Import message"` `action="IMPORTMESSAGE"` `businessObject="Message"`
- `displayName="Trash message"` `action="TRASHMESSAGE"` `businessObject="Message"`
- `displayName="Untrash message"` `action="UNTRASHMESSAGE"` `businessObject="Message"`
- `displayName="Batch delete messages"` `action="BATCHDELETE"` `businessObject="Message"`
- `displayName="Batch modify messages"` `action="BATCHMODIFY"` `businessObject="Message"`
- `displayName="Retrieve attachment"` `action="RETRIEVE"` `businessObject="MessageAttachment"`
- `displayName="List threads"` `action="RETRIEVEALL"` `businessObject="Thread"`
- `displayName="Retrieve thread"` `action="RETRIEVE"` `businessObject="Thread"`
- `displayName="Delete thread"` `action="DELETEALL"` `businessObject="Thread"`
- `displayName="Modify thread"` `action="UPDATEALL"` `businessObject="Thread"`
- `displayName="Trash thread"` `action="TRASHTHREAD"` `businessObject="Thread"`
- `displayName="Untrash thread"` `action="UNTRASHTHREAD"` `businessObject="Thread"`
- `displayName="List labels"` `action="RETRIEVEALL"` `businessObject="Label"`
- `displayName="Create label"` `action="CREATE"` `businessObject="Label"`
- `displayName="Retrieve label"` `action="RETRIEVE"` `businessObject="Label"`
- `displayName="Update label"` `action="UPDATEALL"` `businessObject="Label"`
- `displayName="Delete label"` `action="DELETEALL"` `businessObject="Label"`
- `displayName="List history"` `action="RETRIEVEALL"` `businessObject="History"`
- `displayName="List filters"` `action="RETRIEVEALL"` `businessObject="Filter"`
- `displayName="Create filter"` `action="CREATE"` `businessObject="Filter"`
- `displayName="Retrieve filter"` `action="RETRIEVE"` `businessObject="Filter"`
- `displayName="Delete filter"` `action="DELETEALL"` `businessObject="Filter"`
- `displayName="List send-as aliases"` `action="RETRIEVEALL"` `businessObject="SendAsAlias"`
- `displayName="Create send-as alias"` `action="CREATE"` `businessObject="SendAsAlias"`
- `displayName="Retrieve send-as alias"` `action="RETRIEVE"` `businessObject="SendAsAlias"`
- `displayName="Update send-as alias"` `action="UPDATEALL"` `businessObject="SendAsAlias"`
- `displayName="Delete send-as alias"` `action="DELETEALL"` `businessObject="SendAsAlias"`
- `displayName="Verify send-as alias"` `action="VERIFYSENDAS"` `businessObject="SendAsAlias"`
- `displayName="List S/MIME info"` `action="RETRIEVEALL"` `businessObject="SmimeInfo"`
- `displayName="Retrieve S/MIME info"` `action="RETRIEVE"` `businessObject="SmimeInfo"`
- `displayName="Delete S/MIME info"` `action="DELETEALL"` `businessObject="SmimeInfo"`
- `displayName="Set default S/MIME info"` `action="SETDEFAULT"` `businessObject="SmimeInfo"`
- `displayName="List delegates"` `action="RETRIEVEALL"` `businessObject="Delegate"`
- `displayName="Create delegate"` `action="CREATE"` `businessObject="Delegate"`
- `displayName="Retrieve delegate"` `action="RETRIEVE"` `businessObject="Delegate"`
- `displayName="Delete delegate"` `action="DELETEALL"` `businessObject="Delegate"`
- `displayName="List forwarding addresses"` `action="RETRIEVEALL"` `businessObject="ForwardingAddress"`
- `displayName="Create forwarding address"` `action="CREATE"` `businessObject="ForwardingAddress"`
- `displayName="Retrieve forwarding address"` `action="RETRIEVE"` `businessObject="ForwardingAddress"`
- `displayName="Delete forwarding address"` `action="DELETEALL"` `businessObject="ForwardingAddress"`
- `displayName="List CSE key pairs"` `action="RETRIEVEALL"` `businessObject="CseKeyPair"`
- `displayName="Create CSE key pair"` `action="CREATE"` `businessObject="CseKeyPair"`
- `displayName="Retrieve CSE key pair"` `action="RETRIEVE"` `businessObject="CseKeyPair"`
- `displayName="Disable CSE key pair"` `action="DISABLEKEYPAIR"` `businessObject="CseKeyPair"`
- `displayName="Enable CSE key pair"` `action="ENABLEKEYPAIR"` `businessObject="CseKeyPair"`
- `displayName="Obliterate CSE key pair"` `action="OBLITERATEKEYPAIR"` `businessObject="CseKeyPair"`
- `displayName="List CSE identities"` `action="RETRIEVEALL"` `businessObject="CseIdentity"`
- `displayName="Create CSE identity"` `action="CREATE"` `businessObject="CseIdentity"`
- `displayName="Retrieve CSE identity"` `action="RETRIEVE"` `businessObject="CseIdentity"`
- `displayName="Delete CSE identity"` `action="DELETEALL"` `businessObject="CseIdentity"`

The following combination is allowed for Gmail Input nodes:

- `displayName="New email"` `action="CREATED"` `businessObject="mail"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Gmail1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Gmail1" policyTemplate="online_v1_basic_oauth" policyType="gmail" shortDescription="" version="">
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