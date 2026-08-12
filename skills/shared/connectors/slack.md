# Slack

## Purpose
Connector-specific rules for Slack Request and Slack Input nodes.

## When to use
Use this document when the requested ACE flow includes a Slack Request node or Slack Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Slack Request node
- Slack Input node

## Required node attributes
### Slack Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_slack.msgnode`
- `applicationConnectorType="slack"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Slack Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_slack.msgnode`
- `applicationConnectorType="slack"`

## Schema file requirements
For Slack Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Slack Request nodes:

- `displayName="Create message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Create channel"` `action="CREATE"` `businessObject="Channel"`
- `displayName="Retrieve channels"` `action="RETRIEVEALL"` `businessObject="Channel"`
- `displayName="Retrieve channel"` `action="RETRIEVE"` `businessObject="Channel"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Retrieve group"` `action="RETRIEVE"` `businessObject="Group"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="Group"`
- `displayName="Create file"` `action="CREATE"` `businessObject="File"`
- `displayName="Retrieve files"` `action="RETRIEVEALL"` `businessObject="File"`
- `displayName="Retrieve file"` `action="RETRIEVE"` `businessObject="File"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Retrieve IMs"` `action="RETRIEVEALL"` `businessObject="IM"`
- `displayName="Retrieve IM"` `action="RETRIEVE"` `businessObject="IM"`
- `displayName="Retrieve MPIMs"` `action="RETRIEVEALL"` `businessObject="MPIM"`
- `displayName="Retrieve MPIM"` `action="RETRIEVE"` `businessObject="MPIM"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve user"` `action="RETRIEVE"` `businessObject="User"`
- `displayName="Create user group"` `action="CREATE"` `businessObject="UserGroup"`
- `displayName="Retrieve user groups"` `action="RETRIEVEALL"` `businessObject="UserGroup"`
- `displayName="Update user group"` `action="UPDATEALL"` `businessObject="UserGroup"`

The following combinations are allowed for Slack Input nodes:

- `displayName="New message"` `action="CREATED"` `businessObject="RawMessage"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Slack1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Slack1" policyTemplate="online_v1_basic_oauth" policyType="slack" shortDescription="" version="">
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
