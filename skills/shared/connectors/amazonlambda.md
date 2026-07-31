# Amazon Lambda

## Purpose
Connector-specific rules for Amazon Lambda Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon Lambda Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon Lambda Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazonlambda.msgnode`
- `applicationConnectorType="amazonlambda"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon Lambda Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon Lambda Request nodes:

- `displayName="Create function"` `action="CREATE"` `businessObject="function"`
- `displayName="Retrieve functions"` `action="RETRIEVEALL"` `businessObject="function"`
- `displayName="Update function"` `action="UPDATEALL"` `businessObject="function"`
- `displayName="Delete function"` `action="DELETEALL"` `businessObject="function"`
- `displayName="Invoke function"` `action="INVOKEFUNCTION"` `businessObject="function"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonLambda1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonLambda1" policyTemplate="online_v1_aws_basic_pki" policyType="amazonlambda" shortDescription="" version="">
     <credentialName>AmazonLambdaCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>AWS_BASIC_PKI</authenticationMethod>
     <region/>
     <roleArn/>
     <oidcServerUrl/>
     <profileArn/>
     <trustAnchorArn/>
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
