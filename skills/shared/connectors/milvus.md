# Milvus

## Purpose
Connector-specific rules for Milvus Request nodes.

## When to use
Use this document when the requested ACE flow includes a Milvus Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Milvus Request node

## Connector type
Milvus uses the `appconnectNative` discovery protocol (dynamic OpenAPI connector). Operations are resolved at runtime from the OpenAPI specification. Use the `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Milvus Request nodes:

- `displayName="Retrieve vectors"` `action="retrievewithwhere"` `businessObject="Vectors"`
- `displayName="Insert vector"` `action="create"` `businessObject="Vectors"`
- `displayName="Search vector"` `action="custom"` `businessObject="Vectors"`
- `displayName="Hybrid search vector"` `action="custom"` `businessObject="Vectors"`
- `displayName="Delete vector"` `action="delete"` `businessObject="Vectors"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Milvus1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Milvus1" policyTemplate="online_v1_basic_bearer" policyType="milvus" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_BEARER</authenticationMethod>
        <apiUrl/>
        <acceptSelfSignedCerts>false</acceptSelfSignedCerts>
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
