# Google Groups

## Purpose
Connector-specific rules for Google Groups Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Groups Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Groups Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlegroups.msgnode`
- `applicationConnectorType="googlegroups"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Groups Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Groups Request nodes:

- `displayName="Create group"` `action="CREATE"` `businessObject="Groups"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Groups"`
- `displayName="Retrieve group by ID"` `action="RETRIEVE"` `businessObject="Groups"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="Groups"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="Groups"`
- `displayName="Retrieve group aliases"` `action="RETRIEVEALL"` `businessObject="Group aliases"`
- `displayName="Create group alias"` `action="CREATE"` `businessObject="Group aliases"`
- `displayName="Delete group alias"` `action="DELETEALL"` `businessObject="Group aliases"`
- `displayName="Add member to group"` `action="CREATE"` `businessObject="Group members"`
- `displayName="Retrieve members"` `action="RETRIEVEALL"` `businessObject="Group members"`
- `displayName="Retrieve member by ID"` `action="RETRIEVE"` `businessObject="Group members"`
- `displayName="Update member"` `action="UPDATEALL"` `businessObject="Group members"`
- `displayName="Remove member from group"` `action="DELETEALL"` `businessObject="Group members"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Googlegroups1`.
- Note: this connector uses `authenticationMethod="BASIC_API_KEY"` with service account credentials (user email, service account email, and private key). It also supports `BASIC_OAUTH` and `OAUTH2_WEB` authentication.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Googlegroups1" policyTemplate="online_v1_basic_api_key" policyType="googlegroups" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_API_KEY</authenticationMethod>
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