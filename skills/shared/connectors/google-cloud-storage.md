# Google Cloud Storage

## Purpose
Connector-specific rules for Google Cloud Storage Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Cloud Storage Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Cloud Storage Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlecloudstorage.msgnode`
- `applicationConnectorType="googlecloudstorage"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Cloud Storage Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Cloud Storage Request nodes:

- `displayName="Create bucket"` `action="CREATE"` `businessObject="Bucket"`
- `displayName="Retrieve buckets"` `action="RETRIEVEALL"` `businessObject="Bucket"`
- `displayName="Delete bucket"` `action="DELETEALL"` `businessObject="Bucket"`
- `displayName="Set bucket default storage class"` `action="SETBUCKETDEFAULTSTORAGECLASS"` `businessObject="Bucket"`
- `displayName="Get bucket default storage class"` `action="GETBUCKETDEFAULTSTORAGECLASS"` `businessObject="Bucket"`
- `displayName="Retrieve bucket ACLs"` `action="RETRIEVEALL"` `businessObject="BucketACL"`
- `displayName="Update bucket ACL"` `action="UPDATEBUCKETACL"` `businessObject="BucketACL"`
- `displayName="Get bucket tags"` `action="GETBUCKETTAGS"` `businessObject="BucketTags"`
- `displayName="Set bucket tags"` `action="SETBUCKETTAGS"` `businessObject="BucketTags"`
- `displayName="Retrieve bucket lifecycle configurations"` `action="RETRIEVEALL"` `businessObject="BucketLifecycleConfiguration"`
- `displayName="Update bucket lifecycle configuration"` `action="UPDATEBUCKETLIFECYCLECONFIG"` `businessObject="BucketLifecycleConfiguration"`
- `displayName="Get bucket versioning"` `action="GETBUCKETVERSIONING"` `businessObject="BucketVersioning"`
- `displayName="Set bucket versioning"` `action="SETBUCKETVERSIONING"` `businessObject="BucketVersioning"`
- `displayName="Retrieve bucket CORS configurations"` `action="RETRIEVEALL"` `businessObject="BucketCORSConfiguration"`
- `displayName="Update bucket CORS configuration"` `action="UPDATEBUCKETCORSCONFIG"` `businessObject="BucketCORSConfiguration"`
- `displayName="Retrieve bucket logging configurations"` `action="RETRIEVEALL"` `businessObject="BucketLoggingConfiguration"`
- `displayName="Update bucket logging configuration"` `action="UPDATEBUCKETLOGGINGCONFIGURATION"` `businessObject="BucketLoggingConfiguration"`
- `displayName="Retrieve bucket website"` `action="RETRIEVEALL"` `businessObject="BucketWebsite"`
- `displayName="Update bucket website"` `action="UPDATEBUCKETWEBSITE"` `businessObject="BucketWebsite"`
- `displayName="Retrieve bucket location"` `action="RETRIEVEALL"` `businessObject="BucketLocation"`
- `displayName="Retrieve objects"` `action="RETRIEVEALL"` `businessObject="Object"`
- `displayName="Update or create object"` `action="UPSERTWITHWHERE"` `businessObject="Object"`
- `displayName="Delete object"` `action="DELETEALL"` `businessObject="Object"`
- `displayName="Copy object"` `action="COPYOBJECT"` `businessObject="Object"`
- `displayName="Download object content"` `action="DOWNLOADOBJECTCONTENT"` `businessObject="Object"`
- `displayName="Retrieve object ACL"` `action="RETRIEVEALL"` `businessObject="ObjectACL"`
- `displayName="Update object ACL"` `action="UPDATEOBJECTACL"` `businessObject="ObjectACL"`
- `displayName="Retrieve object versioning"` `action="RETRIEVEALL"` `businessObject="ObjectVersioning"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:GoogleCloudStorage1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="GoogleCloudStorage1" policyTemplate="online_v1_basic" policyType="googlecloudstorage" shortDescription="" version="">
     <credentialName>GoogleCloudStorageCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <bucketName/>
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
