# Amazon EC2

## Purpose
Connector-specific rules for Amazon EC2 Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon EC2 Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon EC2 Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazonec2.msgnode`
- `applicationConnectorType="amazonec2"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon EC2 Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon EC2 Request nodes:

- `displayName="Retrieve instances"` `action="RETRIEVEALL"` `businessObject="Instance"`
- `displayName="Launch instances"` `action="LAUNCHINSTANCES"` `businessObject="Instance"`
- `displayName="Start instances"` `action="STARTINSTANCES"` `businessObject="Instance"`
- `displayName="Stop instances"` `action="STOPINSTANCES"` `businessObject="Instance"`
- `displayName="Reboot instances"` `action="REBOOTINSTANCES"` `businessObject="Instance"`
- `displayName="Terminate instances"` `action="TERMINATEINSTANCES"` `businessObject="Instance"`
- `displayName="Retrieve instance types"` `action="RETRIEVEALL"` `businessObject="InstanceType"`
- `displayName="Retrieve images"` `action="RETRIEVEALL"` `businessObject="Image"`
- `displayName="Retrieve security groups"` `action="RETRIEVEALL"` `businessObject="SecurityGroup"`
- `displayName="Retrieve key pairs"` `action="RETRIEVEALL"` `businessObject="KeyPair"`
- `displayName="Retrieve availability zones"` `action="RETRIEVEALL"` `businessObject="AvailabilityZone"`
- `displayName="Retrieve launch templates"` `action="RETRIEVEALL"` `businessObject="LaunchTemplate"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonEC21`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonEC21" policyTemplate="onprem_v1_aws_basic_pki" policyType="amazonec2" shortDescription="" version="">
     <credentialName>AmazonEC2Credential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>onprem</applicationType>
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
