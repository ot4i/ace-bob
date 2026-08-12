# Zendesk Service

## Purpose
Connector-specific rules for Zendesk Service Request nodes.

## When to use
Use this document when the requested ACE flow includes a Zendesk Service Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Zendesk Service Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_zendeskservice.msgnode`
- `applicationConnectorType="zendeskservice"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Zendesk Service Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Zendesk Service Request nodes:

- `displayName="Create ticket"` `action="CREATE"` `businessObject="Ticket"`
- `displayName="Retrieve tickets"` `action="RETRIEVEALL"` `businessObject="Ticket"`
- `displayName="Update ticket"` `action="UPDATEALL"` `businessObject="Ticket"`
- `displayName="Delete ticket"` `action="DELETEALL"` `businessObject="Ticket"`
- `displayName="Mark ticket as spam and suspend user"` `action="MARKSPAMANDSUSPENDUSER"` `businessObject="Ticket"`
- `displayName="Retrieve attachment"` `action="RETRIEVEALL"` `businessObject="ticketAttachment"`
- `displayName="Upload attachment"` `action="UPLOADATTACHMENT"` `businessObject="ticketAttachment"`
- `displayName="Download attachment"` `action="DOWNLOADTICKETATTACHMENT"` `businessObject="ticketAttachment"`
- `displayName="Redact ticket attachment"` `action="REDACTATTACHMENT"` `businessObject="ticketAttachment"`
- `displayName="Create article"` `action="CREATE"` `businessObject="article"`
- `displayName="Retrieve articles"` `action="RETRIEVEALL"` `businessObject="article"`
- `displayName="Update article"` `action="UPDATEALL"` `businessObject="article"`
- `displayName="Archive article"` `action="ARCHIVEARTICLE"` `businessObject="article"`
- `displayName="Create user"` `action="CREATE"` `businessObject="User"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Update user"` `action="UPDATEALL"` `businessObject="User"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="User"`
- `displayName="Update or create a user"` `action="UPSERTWITHWHERE"` `businessObject="User"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Zendeskservice1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Zendeskservice1" policyTemplate="online_v1_basic" policyType="zendeskservice" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
