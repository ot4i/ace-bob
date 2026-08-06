# IBM Engineering Workflow Management

## Purpose
Connector-specific rules for IBM Engineering Workflow Management Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Engineering Workflow Management Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Engineering Workflow Management Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ibmewm.msgnode`
- `applicationConnectorType="ibmewm"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM Engineering Workflow Management Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance


## Allowed operations
The following combinations are allowed for IBM Engineering Workflow Management Request nodes:

- `displayName="Create attachment"` `action="CREATE"` `businessObject="attachment"`
- `displayName="Download attachment"` `action="DOWNLOADFILE"` `businessObject="attachment"`
- `displayName="Retrieve project areas"` `action="RETRIEVEALL"` `businessObject="project"`
- `displayName="Create work item"` `action="CREATE"` `businessObject="workitem"`
- `displayName="Retrieve work items"` `action="RETRIEVEALL"` `businessObject="workitem"`
- `displayName="Update work item"` `action="UPDATEALL"` `businessObject="workitem"`
- `displayName="Retrieve work item types"` `action="RETRIEVEALL"` `businessObject="workitemtype"`
- `displayName="Resolve resource URI"` `action="GETURI"` `businessObject="uriresolver"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Ibmewm1`.


## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Ibmewm1" policyTemplate="onprem_v1_basic" policyType="ibmewm" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>onprem</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <contextUrl/>
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