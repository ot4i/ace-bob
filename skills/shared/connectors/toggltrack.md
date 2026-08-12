# Toggl Track

## Purpose
Connector-specific rules for Toggl Track Request nodes.

## When to use
Use this document when the requested ACE flow includes a Toggl Track Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Toggl Track Request node

## Required node attributes
### Toggl Track Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_toggltrack.msgnode`
- `applicationConnectorType="toggltrack"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Toggl Track Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Toggl Track Request nodes:

- `displayName="Create client"` `action="CREATE"` `businessObject="Client"`
- `displayName="Retrieve clients"` `action="RETRIEVEALL"` `businessObject="Client"`
- `displayName="Create project"` `action="CREATE"` `businessObject="Project"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Project"`
- `displayName="Create tag"` `action="CREATE"` `businessObject="Tag"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="Tag"`
- `displayName="Create time entry"` `action="CREATE"` `businessObject="TimeEntry"`
- `displayName="Retrieve time entries"` `action="RETRIEVEALL"` `businessObject="TimeEntry"`
- `displayName="Update time entry"` `action="UPDATEALL"` `businessObject="TimeEntry"`
- `displayName="Delete time entry"` `action="DELETEALL"` `businessObject="TimeEntry"`
- `displayName="Retrieve workspace users"` `action="RETRIEVEALL"` `businessObject="WorkspaceUser"`
- `displayName="Create workspace"` `action="CREATE"` `businessObject="Workspace"`
- `displayName="Retrieve workspaces"` `action="RETRIEVEALL"` `businessObject="Workspace"`
- `displayName="Create invitation"` `action="CREATE"` `businessObject="Invitation"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:TogglTrack1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="TogglTrack1" policyTemplate="online_v1_basic" policyType="toggltrack" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl>https://api.track.toggl.com/api/v9</apiUrl>
        <isTlsEnabled>false</isTlsEnabled>
        <endpointUrl/>
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
