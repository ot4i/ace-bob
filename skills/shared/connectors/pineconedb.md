# Pinecone

## Purpose
Connector-specific rules for Pinecone Request nodes.

## When to use
Use this document when the requested ACE flow includes a Pinecone Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Pinecone Request node

## Connector type
Pinecone uses the `appconnectNative` discovery protocol (dynamic OpenAPI connector). Operations are resolved at runtime from the OpenAPI specification. Use the `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Pinecone Request nodes:

- `displayName="Create index"` `action="create"` `businessObject="Indexes"`
- `displayName="Retrieve all indexes"` `action="retrievewithwhere"` `businessObject="Indexes"`
- `displayName="Retrieve index details by name"` `action="retrieve"` `businessObject="Indexes"`
- `displayName="Delete index"` `action="delete"` `businessObject="Indexes"`
- `displayName="Retrieve vector IDs"` `action="retrievewithwhere"` `businessObject="Vectors"`
- `displayName="Query vectors"` `action="custom"` `businessObject="Vectors"`
- `displayName="Update or create vector"` `action="create"` `businessObject="Vectors"`
- `displayName="Delete vectors"` `action="delete"` `businessObject="Vectors"`
- `displayName="Update vector"` `action="update"` `businessObject="Vectors"`
- `displayName="Retrieve vectors"` `action="retrieve"` `businessObject="Vectors"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Pineconedb1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Pineconedb1" policyTemplate="online_v1_basic_api_key" policyType="pineconedb" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <apiUrl>https://api.pinecone.io</apiUrl>
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
