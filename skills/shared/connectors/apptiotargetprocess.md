# IBM Targetprocess

## Purpose
Connector-specific rules for IBM Targetprocess Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Targetprocess Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Targetprocess Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_apptiotargetprocess.msgnode`
- `applicationConnectorType="apptiotargetprocess"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM Targetprocess Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM Targetprocess Request nodes:

- `displayName="Create or update user story"` `action="postApiV1UserStories"` `businessObject="User stories"`
- `displayName="Retrieve user stories"` `action="RETRIEVEALL"` `businessObject="User stories"`
- `displayName="Create or update bug"` `action="postApiV1Bugs"` `businessObject="Bugs"`
- `displayName="Retrieve bugs"` `action="RETRIEVEALL"` `businessObject="Bugs"`
- `displayName="Create or update epic"` `action="postApiV1Epics"` `businessObject="Epics"`
- `displayName="Retrieve epics"` `action="RETRIEVEALL"` `businessObject="Epics"`
- `displayName="Create or update task"` `action="postApiV1Tasks"` `businessObject="Tasks"`
- `displayName="Retrieve tasks"` `action="RETRIEVEALL"` `businessObject="Tasks"`
- `displayName="Create or update comment"` `action="postApiV1Comments"` `businessObject="Comments"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="Comments"`
- `displayName="Create or update feature"` `action="postApiV1Features"` `businessObject="Features"`
- `displayName="Retrieve features"` `action="RETRIEVEALL"` `businessObject="Features"`
- `displayName="Create or update project"` `action="postApiV1Projects"` `businessObject="Projects"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Projects"`
- `displayName="Create or update user"` `action="postApiV1Users"` `businessObject="Users"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="Users"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Apptiotargetprocess1`.
- This connector uses `applicationType="online"` and `authenticationMethod="BASIC"`. The policy includes an `<apiUrl>` field for the server URL, an `<isTlsEnabled>` field, and an `<endpointUrl>` field for overriding the server URL.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Apptiotargetprocess1" policyTemplate="online_v1_basic" policyType="apptiotargetprocess" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
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
