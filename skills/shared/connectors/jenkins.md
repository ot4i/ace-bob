# Jenkins

## Purpose
Connector-specific rules for Jenkins Request nodes.

## When to use
Use this document when the requested ACE flow includes a Jenkins Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Jenkins Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_jenkins.msgnode`
- `applicationConnectorType="jenkins"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Jenkins Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Jenkins Request nodes:

- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="project"`
- `displayName="Delete project"` `action="DELETEALL"` `businessObject="project"`
- `displayName="Enable project"` `action="ENABLE_JOB"` `businessObject="project"`
- `displayName="Disable project"` `action="DISABLE_JOB"` `businessObject="project"`
- `displayName="Verify whether project exists"` `action="VERIFY_JOB"` `businessObject="project"`
- `displayName="Retrieve builds"` `action="RETRIEVEALL"` `businessObject="build"`
- `displayName="Delete build"` `action="DELETEALL"` `businessObject="build"`
- `displayName="Get queued build information"` `action="GET_QUEUE_INFO"` `businessObject="build"`
- `displayName="Start build"` `action="START_BUILD"` `businessObject="build"`
- `displayName="Stop build"` `action="STOP_BUILD"` `businessObject="build"`
- `displayName="Cancel queued build"` `action="CANCEL_QUEUE_BUILD"` `businessObject="build"`
- `displayName="Download console output"` `action="DOWNLOAD_CONSOLE_OUTPUT"` `businessObject="build"`
- `displayName="Download build artifacts"` `action="DOWNLOAD_BUILD_ARTIFACTS"` `businessObject="build"`
- `displayName="Get last build"` `action="GET_LAST_BUILD"` `businessObject="build"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Jenkins1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Jenkins1" policyTemplate="online_v1_basic" policyType="jenkins" shortDescription="" version="">
     <credentialName>JenkinsCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <endpointUrl>https://123.45.123.45</endpointUrl>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
