# Crystal Ball

## Purpose
Connector-specific rules for Crystal Ball Request nodes.

## When to use
Use this document when the requested ACE flow includes a Crystal Ball Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Crystal Ball Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_crystalball.msgnode`
- `applicationConnectorType="crystalball"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Crystal Ball Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Crystal Ball Request nodes:

- `displayName="Retrieve annotations"` `action="RETRIEVEWITHWHERE"` `businessObject="Annotations"`
- `displayName="Create annotation"` `action="CREATE"` `businessObject="Annotations"`
- `displayName="Update annotation"` `action="UPDATE"` `businessObject="Annotations"`
- `displayName="Delete annotation"` `action="DELETE"` `businessObject="Annotations"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:CrystalBall1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="CrystalBall1" policyTemplate="online_v1_basic_bearer" policyType="crystalball" shortDescription="" version="">
        <credentialName>CrystalBallCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_BEARER</authenticationMethod>
        <apiUrl>https://app.crystalballinsight.com</apiUrl>
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
