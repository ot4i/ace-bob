# IBM z/OS Connect

## Purpose
Connector-specific rules for IBM z/OS Connect Request and IBM z/OS Connect Input nodes.

## When to use
Use this document when the requested ACE flow includes an IBM z/OS Connect Request node or IBM z/OS Connect Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM z/OS Connect Request node
- IBM z/OS Connect Input node

## Required node attributes
### IBM z/OS Connect Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_zosconnect.msgnode`
- `applicationConnectorType="zosconnect"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### IBM z/OS Connect Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_zosconnect.msgnode`
- `applicationConnectorType="zosconnect"`

## Schema file requirements
For IBM z/OS Connect Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The IBM z/OS Connect connector is a dynamic connector. Operations are not fixed at build time — they are discovered at runtime from the annotated OpenAPI specification exposed by the connected z/OS Connect endpoint. The available `action` and `businessObject` values will therefore vary depending on the APIs registered on the target z/OS Connect server.

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:ZOSConnect1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="ZOSConnect1" policyTemplate="online_v1_basic" policyType="zosconnect" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
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
