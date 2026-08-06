# Google Chat

## Purpose
Connector-specific rules for Google Chat Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Chat Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Chat Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlechat.msgnode`
- `applicationConnectorType="googlechat"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Chat Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Chat Request nodes:

- `displayName="Create space"` `action="CREATE"` `businessObject="Spaces"`
- `displayName="Retrieve spaces"` `action="RETRIEVEALL"` `businessObject="Spaces"`
- `displayName="Search direct message space"` `action="FINDDIRECTMESSAGE"` `businessObject="Spaces"`
- `displayName="Retrieve space by ID"` `action="RETRIEVE"` `businessObject="Spaces"`
- `displayName="Delete space"` `action="DELETEALL"` `businessObject="Spaces"`
- `displayName="Update space"` `action="UPDATEALL"` `businessObject="Spaces"`
- `displayName="Send message"` `action="CREATE"` `businessObject="Messages"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Messages"`
- `displayName="Delete message"` `action="DELETEALL"` `businessObject="Messages"`
- `displayName="Update message"` `action="UPDATEALL"` `businessObject="Messages"`
- `displayName="Retrieve message by ID"` `action="RETRIEVE"` `businessObject="Messages"`
- `displayName="Add member to space"` `action="ADDMEMBER"` `businessObject="Members"`
- `displayName="Retrieve members"` `action="RETRIEVEALL"` `businessObject="Members"`
- `displayName="Retrieve member by ID"` `action="RETRIEVE"` `businessObject="Members"`
- `displayName="Remove member from space"` `action="DELETEALL"` `businessObject="Members"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Googlechat1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Googlechat1" policyTemplate="online_v1_basic_oauth" policyType="googlechat" shortDescription="" version="">
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