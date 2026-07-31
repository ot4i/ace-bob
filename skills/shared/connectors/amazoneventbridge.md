# Amazon EventBridge

## Purpose
Connector-specific rules for Amazon EventBridge Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon EventBridge Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon EventBridge Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazoneventbridge.msgnode`
- `applicationConnectorType="amazoneventbridge"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon EventBridge Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon EventBridge Request nodes:

- `displayName="Create event bus"` `action="CREATE"` `businessObject="eventBus"`
- `displayName="Retrieve event buses"` `action="RETRIEVEALL"` `businessObject="eventBus"`
- `displayName="Delete event bus"` `action="DELETEALL"` `businessObject="eventBus"`
- `displayName="Send events"` `action="SENDEVENT"` `businessObject="event"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonEventBridge1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonEventBridge1" policyTemplate="onprem_v1_aws_basic_pki" policyType="amazoneventbridge" shortDescription="" version="">
     <credentialName>AmazonEventBridgeCredential</credentialName>
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
