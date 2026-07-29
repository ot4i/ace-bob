# Dropbox

## Purpose
Connector-specific rules for Dropbox Request nodes.

## When to use
Use this document when the requested ACE flow includes a Dropbox Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Dropbox Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_dropbox.msgnode`
- `applicationConnectorType="dropbox"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Dropbox Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Dropbox Request nodes:

- `displayName="Create Team Group"` `action="CREATE"` `businessObject="teamgroups"`
- `displayName="Retrieve all team groups"` `action="RETRIEVEALL"` `businessObject="teamgroups"`
- `displayName="Updates a group's name and/or external ID."` `action="UPDATEALL"` `businessObject="teamgroups"`
- `displayName="Delete Teams group"` `action="DELETEALL"` `businessObject="teamgroups"`
- `displayName="Add Team Group Member"` `action="ADDGROUPMEMBERS"` `businessObject="teamgroups"`
- `displayName="Retrieve all team group members"` `action="LISTGROUPMEMBERS"` `businessObject="teamgroups"`
- `displayName="Delete Teams group member"` `action="REMOVEGROUPMEMBERS"` `businessObject="teamgroups"`
- `displayName="Add Team Member"` `action="CREATE"` `businessObject="teammembers"`
- `displayName="Retrieve team members"` `action="RETRIEVEALL"` `businessObject="teammembers"`
- `displayName="Delete Teams Member"` `action="DELETEALL"` `businessObject="teammembers"`
- `displayName="Namespaces List"` `action="RETRIEVEALL"` `businessObject="namespaces"`
- `displayName="Retrieve team folders"` `action="RETRIEVEALL"` `businessObject="teamfolders"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Dropbox1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Dropbox1" policyTemplate="online_v1_basic_oauth" policyType="dropbox" shortDescription="" version="">
     <credentialName>DropboxCredential</credentialName>
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
