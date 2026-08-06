# IBM Cloud Object Storage S3

## Purpose
Connector-specific rules for IBM Cloud Object Storage S3 Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Cloud Object Storage S3 Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Cloud Object Storage S3 Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ibmcoss3.msgnode`
- `applicationConnectorType="ibmcoss3"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM Cloud Object Storage S3 Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for IBM Cloud Object Storage S3 Request nodes:

- `displayName="Create bucket"` `action="CREATE"` `businessObject="bucket"`
- `displayName="Retrieve buckets"` `action="RETRIEVEALL"` `businessObject="bucket"`
- `displayName="Delete bucket"` `action="DELETEALL"` `businessObject="bucket"`
- `displayName="Create object"` `action="CREATE"` `businessObject="object"`
- `displayName="Retrieve objects"` `action="RETRIEVEALL"` `businessObject="object"`
- `displayName="Update object"` `action="UPDATEALL"` `businessObject="object"`
- `displayName="Delete object"` `action="DELETEALL"` `businessObject="object"`
- `displayName="Update or create object"` `action="UPSERTWITHWHERE"` `businessObject="object"`
- `displayName="Download object"` `action="DOWNLOAD_OBJECT"` `businessObject="object"`
- `displayName="Retrieve object by marker"` `action="RETRIEVE_OBJECT_BY_MARKER"` `businessObject="object"`
- `displayName="Create or update CORS configuration"` `action="CREATE"` `businessObject="cors"`
- `displayName="Retrieve CORS configuration"` `action="RETRIEVEALL"` `businessObject="cors"`
- `displayName="Delete CORS configuration"` `action="DELETEALL"` `businessObject="cors"`
- `displayName="Create standard ACL for bucket"` `action="CREATE_STANDARD_ACL_FOR_BUCKET"` `businessObject="bucketAcl"`
- `displayName="Create custom ACL for bucket"` `action="CREATE_CUSTOM_ACL_FOR_BUCKET"` `businessObject="bucketAcl"`
- `displayName="Retrieve ACL for bucket"` `action="RETRIEVE_ACL_FOR_BUCKET"` `businessObject="bucketAcl"`
- `displayName="Create standard ACL for object"` `action="CREATE_STANDARD_ACL_FOR_OBJECT"` `businessObject="objectAcl"`
- `displayName="Create custom ACL for object"` `action="CREATE_CUSTOM_ACL_FOR_OBJECT"` `businessObject="objectAcl"`
- `displayName="Retrieve ACL for object"` `action="RETRIEVE_ACL_FOR_OBJECT"` `businessObject="objectAcl"`
- `displayName="Retrieve object by prefix and delimiter"` `action="RETRIEVE_OBJECT_BY_PREFIX_DELIMITER"` `businessObject="searchObject"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Ibmcoss31`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Ibmcoss31" policyTemplate="online_v1_basic" policyType="ibmcoss3" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <region/>
        <instanceId/>
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