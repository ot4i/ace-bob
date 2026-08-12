# Vespa

## Purpose
Connector-specific rules for Vespa Request nodes.

## When to use
Use this document when the requested ACE flow includes a Vespa Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Vespa Request node

## Connector type
Vespa uses the `appconnectNative` discovery protocol (dynamic OpenAPI connector). Operations are resolved at runtime from the OpenAPI specification. Use the `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Vespa Request nodes:

- `displayName="Query documents"` `action="custom"` `businessObject="Documents"`
- `displayName="Retrieve documents"` `action="retrievewithwhere"` `businessObject="Documents"`
- `displayName="Retrieve document by filters"` `action="retrieve"` `businessObject="Documents"`
- `displayName="Create document"` `action="custom"` `businessObject="Documents"`
- `displayName="Update or create document"` `action="upsertwithwhere"` `businessObject="Documents"`
- `displayName="Update document"` `action="update"` `businessObject="Documents"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Vespa1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Vespa1" policyTemplate="online_v1_basic_bearer" policyType="vespa" shortDescription="" version="">
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
