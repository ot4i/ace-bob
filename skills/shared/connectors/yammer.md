# Viva Engage

## Purpose
Connector-specific rules for Viva Engage Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes a Viva Engage Request node or a Viva Engage Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Viva Engage Request node
- Viva Engage Input node

## Required node attributes
### Viva Engage Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_yammer.msgnode`
- `applicationConnectorType="yammer"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Viva Engage Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_yammer.msgnode`
- `applicationConnectorType="yammer"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Viva Engage Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

For Viva Engage Input nodes:
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Viva Engage Request nodes:

- `displayName="Create message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Retrieve message"` `action="RETRIEVE"` `businessObject="Message"`
- `displayName="Delete message"` `action="DELETEALL"` `businessObject="Message"`
- `displayName="Create user"` `action="CREATE"` `businessObject="User"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve user"` `action="RETRIEVE"` `businessObject="User"`
- `displayName="Update user"` `action="UPDATEALL"` `businessObject="User"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="User"`
- `displayName="Create pending attachment"` `action="CREATE"` `businessObject="PendingAttachment"`
- `displayName="Retrieve topic"` `action="RETRIEVE"` `businessObject="Topic"`
- `displayName="Retrieve topics"` `action="RETRIEVEALL"` `businessObject="Topic"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Retrieve networks"` `action="RETRIEVEALL"` `businessObject="Network"`

The following combinations are allowed for Viva Engage Input nodes:

- `displayName="New user"` `action="CREATED"` `businessObject="User"`
- `displayName="Deleted user"` `action="DELETED"` `businessObject="User"`
- `displayName="New file"` `action="CREATED"` `businessObject="File"`
- `displayName="New group"` `action="CREATED"` `businessObject="Group"`
- `displayName="Updated group"` `action="UPDATED"` `businessObject="Group"`
- `displayName="New topic"` `action="CREATED"` `businessObject="Topic"`
- `displayName="New message"` `action="CREATED"` `businessObject="Message"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Yammer1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Yammer1" policyTemplate="online_v1_basic_oauth" policyType="yammer" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <endpointUrl>https://www.yammer.com/api/</endpointUrl>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
