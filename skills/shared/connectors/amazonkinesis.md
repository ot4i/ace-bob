# Amazon Kinesis

## Purpose
Connector-specific rules for Amazon Kinesis Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon Kinesis Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon Kinesis Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazonkinesis.msgnode`
- `applicationConnectorType="amazonkinesis"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon Kinesis Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon Kinesis Request nodes:

- `displayName="Create data stream"` `action="CREATE"` `businessObject="dataStream"`
- `displayName="Retrieve data streams"` `action="RETRIEVEALL"` `businessObject="dataStream"`
- `displayName="Delete data stream"` `action="DELETEALL"` `businessObject="dataStream"`
- `displayName="Update stream mode"` `action="UPDATESTREAMMODE"` `businessObject="dataStream"`
- `displayName="Update shard count"` `action="UPDATESHARDCOUNT"` `businessObject="dataStream"`
- `displayName="Increase stream retention period"` `action="INCREASESTREAMRETENTIONPERIOD"` `businessObject="dataStream"`
- `displayName="Decrease stream retention period"` `action="DECREASESTREAMRETENTIONPERIOD"` `businessObject="dataStream"`
- `displayName="Create delivery stream"` `action="CREATE"` `businessObject="deliveryStream"`
- `displayName="Retrieve delivery streams"` `action="RETRIEVEALL"` `businessObject="deliveryStream"`
- `displayName="Delete delivery stream"` `action="DELETEALL"` `businessObject="deliveryStream"`
- `displayName="Add multiple records"` `action="PUTRECORDS"` `businessObject="deliveryStream"`
- `displayName="Update destination"` `action="UPDATEDESTINATION"` `businessObject="deliveryStream"`
- `displayName="Retrieve shards"` `action="RETRIEVEALL"` `businessObject="shard"`
- `displayName="Merge shards"` `action="MERGESHARDS"` `businessObject="shard"`
- `displayName="Split shard"` `action="SPLITSHARD"` `businessObject="shard"`
- `displayName="Get shard iterator"` `action="GETSHARDITERATOR"` `businessObject="shard"`
- `displayName="Retrieve applications"` `action="RETRIEVEALL"` `businessObject="application"`
- `displayName="Start application"` `action="STARTAPPLICATION"` `businessObject="application"`
- `displayName="Stop application"` `action="STOPAPPLICATION"` `businessObject="application"`
- `displayName="Retrieve application snapshots"` `action="RETRIEVEALL"` `businessObject="applicationSnapshot"`
- `displayName="Retrieve application versions"` `action="RETRIEVEALL"` `businessObject="applicationVersion"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="tag"`
- `displayName="Add tags"` `action="ADDTAGS"` `businessObject="tag"`
- `displayName="Remove tags"` `action="REMOVETAGS"` `businessObject="tag"`
- `displayName="Retrieve data stream records"` `action="RETRIEVEALL"` `businessObject="dataStreamRecord"`
- `displayName="Add record"` `action="PUTRECORD"` `businessObject="dataStreamRecord"`
- `displayName="Add multiple records"` `action="PUTRECORDS"` `businessObject="dataStreamRecord"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonKinesis1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonKinesis1" policyTemplate="onprem_v1_aws_basic_pki" policyType="amazonkinesis" shortDescription="" version="">
     <credentialName>AmazonKinesisCredential</credentialName>
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
