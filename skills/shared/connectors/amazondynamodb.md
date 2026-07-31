# Amazon DynamoDB

## Purpose
Connector-specific rules for Amazon DynamoDB Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon DynamoDB Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon DynamoDB Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazondynamodb.msgnode`
- `applicationConnectorType="amazondynamodb"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon DynamoDB Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon DynamoDB Request nodes:

- `displayName="Create table"` `action="CREATE"` `businessObject="table"`
- `displayName="Retrieve tables"` `action="RETRIEVEALL"` `businessObject="table"`
- `displayName="Delete table"` `action="DELETEALL"` `businessObject="table"`
- `displayName="Retrieve items"` `action="RETRIEVEALL"` `businessObject="item"`
- `displayName="Update or create item"` `action="UPSERTWITHWHERE"` `businessObject="item"`
- `displayName="Delete item"` `action="DELETEALL"` `businessObject="item"`
- `displayName="Create bulk items"` `action="BULKCREATE"` `businessObject="item"`
- `displayName="Update bulk items"` `action="BULKUPDATE"` `businessObject="item"`
- `displayName="Delete bulk items"` `action="BULKDELETE"` `businessObject="item"`
- `displayName="Create backup"` `action="CREATE"` `businessObject="backup"`
- `displayName="Retrieve backups"` `action="RETRIEVEALL"` `businessObject="backup"`
- `displayName="Delete backup"` `action="DELETEALL"` `businessObject="backup"`
- `displayName="Restore table from backup"` `action="RESTORETABLEFROMBACKUP"` `businessObject="backup"`
- `displayName="Get continuous backup information"` `action="GETCONTINUOUSBACKUPINFO"` `businessObject="backup"`
- `displayName="Add or remove continuous backup"` `action="ADDORREMOVECONTINUOUSBACKUP"` `businessObject="backup"`
- `displayName="Restore table to point in time"` `action="RESTORETABLE"` `businessObject="backup"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="tag"`
- `displayName="Add tags"` `action="ADDTAGS"` `businessObject="tag"`
- `displayName="Remove tags"` `action="REMOVETAGS"` `businessObject="tag"`
- `displayName="Get limits"` `action="GETLIMITS"` `businessObject="region"`
- `displayName="Add or remove time to live"` `action="ADDREMOVETTL"` `businessObject="addremovettl"`
- `displayName="Get time to live"` `action="GETTTL"` `businessObject="getttl"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonDynamoDB1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonDynamoDB1" policyTemplate="online_v1_aws_basic_pki" policyType="amazondynamodb" shortDescription="" version="">
     <credentialName>AmazonDynamoDBCredential</credentialName>
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
