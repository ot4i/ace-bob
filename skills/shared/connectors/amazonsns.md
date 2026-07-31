# Amazon SNS

## Purpose
Connector-specific rules for Amazon SNS Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon SNS Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon SNS Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazonsns.msgnode`
- `applicationConnectorType="amazonsns"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon SNS Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon SNS Request nodes:

- `displayName="Create topic"` `action="CREATE"` `businessObject="Topic"`
- `displayName="Delete topic"` `action="DELETEALL"` `businessObject="Topic"`
- `displayName="Publish message to topic"` `action="PUBLISHMESSAGEONTOPIC"` `businessObject="Topic"`
- `displayName="Retrieve topics"` `action="RETRIEVEALL"` `businessObject="Topic"`
- `displayName="Update topic"` `action="UPDATEALL"` `businessObject="Topic"`
- `displayName="Create subscription"` `action="CREATE"` `businessObject="Subscription"`
- `displayName="Confirm subscription"` `action="CONFIRMSUBSCRIPTION"` `businessObject="Subscription"`
- `displayName="Delete subscription"` `action="DELETEALL"` `businessObject="Subscription"`
- `displayName="Retrieve subscriptions"` `action="RETRIEVEALL"` `businessObject="Subscription"`
- `displayName="Update subscription"` `action="UPDATEALL"` `businessObject="Subscription"`
- `displayName="Create tag"` `action="CREATE"` `businessObject="Tag"`
- `displayName="Delete tag"` `action="DELETEALL"` `businessObject="Tag"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="Tag"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonSNS1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonSNS1" policyTemplate="online_v1_aws_basic_pki" policyType="amazonsns" shortDescription="" version="">
     <credentialName>AmazonSNSCredential</credentialName>
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
