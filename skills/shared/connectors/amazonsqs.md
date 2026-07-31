# Amazon SQS

## Purpose
Connector-specific rules for Amazon SQS Request and Amazon SQS Input nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon SQS Request node or Amazon SQS Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon SQS Request node
- Amazon SQS Input node

## Required node attributes
### Amazon SQS Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazonsqs.msgnode`
- `applicationConnectorType="amazonsqs"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Amazon SQS Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_amazonsqs.msgnode`
- `applicationConnectorType="amazonsqs"`

## Schema file requirements
For Amazon SQS Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon SQS Request nodes:

- `displayName="Create queue"` `action="CREATE"` `businessObject="Queue"`
- `displayName="Delete queue"` `action="DELETEALL"` `businessObject="Queue"`
- `displayName="Update queue"` `action="UPDATEALL"` `businessObject="Queue"`
- `displayName="Retrieve queues"` `action="RETRIEVEALL"` `businessObject="Queue"`
- `displayName="Get queue URL"` `action="GETQUEUEURL"` `businessObject="Queue"`
- `displayName="Update policy"` `action="UPDATEPOLICY"` `businessObject="Queue"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="Tags"`
- `displayName="Add tags"` `action="ADDTAGS"` `businessObject="Tags"`
- `displayName="Remove tags"` `action="REMOVETAGS"` `businessObject="Tags"`
- `displayName="Purge queue"` `action="PURGEQUEUE"` `businessObject="PurgeQueue"`
- `displayName="Put message on queue"` `action="PUTMESSAGE"` `businessObject="Messages"`
- `displayName="Remove message from queue"` `action="REMOVEMESSAGE"` `businessObject="Messages"`
- `displayName="Get messages"` `action="GETMESSAGES"` `businessObject="Messages"`
- `displayName="Send bulk messages to queue"` `action="BULKCREATEMESSAGES"` `businessObject="Messages"`
- `displayName="Delete bulk messages from queue"` `action="BULKDELETEMESSAGES"` `businessObject="Messages"`
- `displayName="Change message visibility"` `action="CHANGEMESSAGEVISIBILITY"` `businessObject="ChangeMessageVisibility"`
- `displayName="Change bulk message visibility"` `action="BULKUPDATEMESSAGESVISIBILITY"` `businessObject="ChangeMessageVisibility"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonSQS1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonSQS1" policyTemplate="online_v1_aws_basic_pki" policyType="amazonsqs" shortDescription="" version="">
     <credentialName>AmazonSQSCredential</credentialName>
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
