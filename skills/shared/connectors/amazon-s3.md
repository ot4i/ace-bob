# Amazon S3

## Purpose
Connector-specific rules for Amazon S3 Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon S3 Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon S3 Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazons3.msgnode`
- `applicationConnectorType="amazons3"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon S3 Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon S3 Request nodes:

- `displayName="Retrieve all buckets"` `action="RETRIEVEALL"` `businessObject="bucketcollection"`
- `displayName="Retrieve all objects"` `action="RETRIEVEALL"` `businessObject="objectcollection"`
- `displayName="Update or create object"` `action="UPSERTWITHWHERE"` `businessObject="object"`
- `displayName="Delete object"` `action="DELETEALL"` `businessObject="object"`
- `displayName="Retrieve object metadata"` `action="RETRIEVEALL"` `businessObject="object"`
- `displayName="Retrieve object content"` `action="DOWNLOAD_OBJECT"` `businessObject="object"`
- `displayName="Copy object"` `action="COPY_OBJECT"` `businessObject="object"`
- `displayName="Create object"` `action="CREATE"` `businessObject="object"`
- `displayName="Create bucket"` `action="CREATE"` `businessObject="bucket"`
- `displayName="Retrieve buckets"` `action="RETRIEVEALL"` `businessObject="bucket"`
- `displayName="Delete bucket"` `action="DELETEALL"` `businessObject="bucket"`
- `displayName="Retrieve bucket CORS configuration"` `action="RETRIEVEALL"` `businessObject="cors"`
- `displayName="Delete bucket CORS configuration"` `action="DELETEALL"` `businessObject="cors"`
- `displayName="Update CORS configuration of bucket"` `action="UPSERT_BUCKET_CORS"` `businessObject="cors"`
- `displayName="Retrieve bucket ACL"` `action="RETRIEVEALL"` `businessObject="bucketacl"`
- `displayName="Update bucket ACL"` `action="UPDATEALL"` `businessObject="bucketacl"`
- `displayName="Retrieve object ACL"` `action="RETRIEVEALL"` `businessObject="objectacl"`
- `displayName="Update object ACL"` `action="UPDATEALL"` `businessObject="objectacl"`
- `displayName="Retrieve object tags"` `action="RETRIEVEALL"` `businessObject="objecttags"`
- `displayName="Update object tags"` `action="UPSERT_OBJECT_TAGS"` `businessObject="objecttags"`
- `displayName="Delete object tags"` `action="DELETEALL"` `businessObject="objecttags"`
- `displayName="Retrieve bucket tags"` `action="RETRIEVEALL"` `businessObject="buckettags"`
- `displayName="Update bucket tags"` `action="UPSERT_BUCKET_TAGS"` `businessObject="buckettags"`
- `displayName="Delete bucket tags"` `action="DELETEALL"` `businessObject="buckettags"`
- `displayName="Retrieve bucket website hosting configuration"` `action="RETRIEVEALL"` `businessObject="bucketwebsite"`
- `displayName="Update bucket website hosting configuration"` `action="UPSERT_BUCKET_WEBSITE"` `businessObject="bucketwebsite"`
- `displayName="Delete bucket website hosting configuration"` `action="DELETEALL"` `businessObject="bucketwebsite"`
- `displayName="Retrieve bucket requester payment configuration"` `action="RETRIEVEALL"` `businessObject="bucketrequestpayment"`
- `displayName="Update bucket requester payment configuration"` `action="UPDATEALL"` `businessObject="bucketrequestpayment"`
- `displayName="Retrieve bucket default encryption configuration"` `action="RETRIEVEALL"` `businessObject="bucketencryption"`
- `displayName="Update bucket default encryption configuration"` `action="UPSERT_BUCKET_ENCRYPTION"` `businessObject="bucketencryption"`
- `displayName="Delete bucket default encryption configuration"` `action="DELETEALL"` `businessObject="bucketencryption"`
- `displayName="Retrieve bucket lifecycle configuration"` `action="RETRIEVEALL"` `businessObject="bucketlifecycleconfiguration"`
- `displayName="Update bucket lifecycle configuration"` `action="UPSERT_BUCKET_LIFECYCLE_CONFIGURATION"` `businessObject="bucketlifecycleconfiguration"`
- `displayName="Delete bucket lifecycle configuration"` `action="DELETEALL"` `businessObject="bucketlifecycleconfiguration"`
- `displayName="Retrieve bucket policy"` `action="RETRIEVEALL"` `businessObject="bucketpolicy"`
- `displayName="Update bucket policy"` `action="UPSERT_BUCKET_POLICY"` `businessObject="bucketpolicy"`
- `displayName="Delete bucket policy"` `action="DELETEALL"` `businessObject="bucketpolicy"`
- `displayName="Retrieve bucket inventory configuration"` `action="RETRIEVEALL"` `businessObject="bucketinventoryconfiguration"`
- `displayName="Update or create bucket inventory configuration"` `action="UPSERTWITHWHERE"` `businessObject="bucketinventoryconfiguration"`
- `displayName="Delete bucket inventory configuration"` `action="DELETEALL"` `businessObject="bucketinventoryconfiguration"`
- `displayName="Retrieve bucket metrics configuration"` `action="RETRIEVEALL"` `businessObject="bucketmetricsconfiguration"`
- `displayName="Update or create bucket metrics configuration"` `action="UPSERTWITHWHERE"` `businessObject="bucketmetricsconfiguration"`
- `displayName="Delete bucket metrics configuration"` `action="DELETEALL"` `businessObject="bucketmetricsconfiguration"`
- `displayName="Retrieve bucket analytics configuration"` `action="RETRIEVEALL"` `businessObject="bucketanalyticsconfiguration"`
- `displayName="Update or create analytics configuration for bucket"` `action="UPSERTWITHWHERE"` `businessObject="bucketanalyticsconfiguration"`
- `displayName="Delete bucket analytics configuration"` `action="DELETEALL"` `businessObject="bucketanalyticsconfiguration"`
- `displayName="Retrieve bucket replication configuration"` `action="RETRIEVEALL"` `businessObject="bucketreplication"`
- `displayName="Update bucket replication configuration"` `action="UPSERT_BUCKET_REPLICATION"` `businessObject="bucketreplication"`
- `displayName="Delete bucket replication configuration"` `action="DELETEALL"` `businessObject="bucketreplication"`
- `displayName="Retrieve bucket transfer acceleration configuration"` `action="RETRIEVEALL"` `businessObject="bucketaccelerateconfiguration"`
- `displayName="Update bucket transfer acceleration configuration"` `action="UPDATEALL"` `businessObject="bucketaccelerateconfiguration"`
- `displayName="Retrieve bucket server access logging"` `action="RETRIEVEALL"` `businessObject="bucketlogging"`
- `displayName="Update bucket server access logging"` `action="UPDATEALL"` `businessObject="bucketlogging"`
- `displayName="Retrieve bucket event configuration"` `action="RETRIEVEALL"` `businessObject="bucketnotificationconfiguration"`
- `displayName="Update bucket event configuration"` `action="UPDATEALL"` `businessObject="bucketnotificationconfiguration"`
- `displayName="Retrieve object torrent"` `action="RETRIEVEALL"` `businessObject="objecttorrent"`
- `displayName="Retrieve object versions"` `action="RETRIEVEALL"` `businessObject="objectversioning"`
- `displayName="Update bucket versioning status"` `action="UPDATEALL"` `businessObject="bucketversioning"`
- `displayName="Retrieve bucket versioning status"` `action="RETRIEVEALL"` `businessObject="bucketversioning"`
- `displayName="Retrieve bucket location"` `action="RETRIEVEALL"` `businessObject="bucketlocation"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonS31`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonS31" policyTemplate="online_v1_aws_basic_pki" policyType="amazons3" shortDescription="" version="">
     <credentialName>AmazonS3Credential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>AWS_BASIC_PKI</authenticationMethod>
     <roleArn/>
     <region/>
     <hostname/>
     <bucketName/>
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
