# Microsoft Azure Blob Storage

## Purpose
Connector-specific rules for Microsoft Azure Blob Storage Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Azure Blob Storage Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Azure Blob Storage Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_azureblobstorage.msgnode`
- `applicationConnectorType="azureblobstorage"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft Azure Blob Storage Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Azure Blob Storage Request nodes:

- `displayName="Create container"` `action="CREATE"` `businessObject="container"`
- `displayName="Retrieve containers"` `action="RETRIEVEALL"` `businessObject="container"`
- `displayName="Delete container"` `action="DELETEALL"` `businessObject="container"`
- `displayName="Set container metadata"` `action="SETCONTAINERMETADATA"` `businessObject="container"`
- `displayName="Check container exists"` `action="EXISTS"` `businessObject="container"`
- `displayName="Set container ACL"` `action="SETCONTAINERACL"` `businessObject="container"`
- `displayName="Get container ACL"` `action="GETCONTAINERACL"` `businessObject="container"`
- `displayName="Retrieve blobs"` `action="RETRIEVEALL"` `businessObject="blob"`
- `displayName="Update or create blob"` `action="UPSERTWITHWHERE"` `businessObject="blob"`
- `displayName="Delete blob"` `action="DELETEALL"` `businessObject="blob"`
- `displayName="Copy blob"` `action="COPYBLOB"` `businessObject="blob"`
- `displayName="Set blob metadata"` `action="SETBLOBMETADATA"` `businessObject="blob"`
- `displayName="Check blob exists"` `action="BLOBEXISTS"` `businessObject="blob"`
- `displayName="Download blob content"` `action="DOWNLOADBLOBCONTENT"` `businessObject="blob"`
- `displayName="Abort copy blob"` `action="ABORTCOPYBLOB"` `businessObject="blob"`
- `displayName="Create blob snapshot"` `action="CREATE"` `businessObject="snapshot"`
- `displayName="Retrieve blob snapshots"` `action="RETRIEVEALL"` `businessObject="snapshot"`
- `displayName="Delete blob snapshot"` `action="DELETEALL"` `businessObject="snapshot"`
- `displayName="Retrieve blob versions"` `action="RETRIEVEALL"` `businessObject="version"`
- `displayName="Delete blob version"` `action="DELETEALL"` `businessObject="version"`
- `displayName="Update or create page blob"` `action="UPSERTWITHWHERE"` `businessObject="pageBlob"`
- `displayName="Add page"` `action="APPENDPAGES"` `businessObject="pageBlob"`
- `displayName="Update or create append blob"` `action="UPSERTWITHWHERE"` `businessObject="appendBlob"`
- `displayName="Append block"` `action="APPENDBLOCK"` `businessObject="appendBlob"`
- `displayName="Set blob service properties"` `action="SETBLOBSERVICEPROPERTIES"` `businessObject="blobService"`
- `displayName="Get blob service properties"` `action="GETBLOBSERVICEPROPERTIES"` `businessObject="blobService"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MicrosoftAzureBlobstorage1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="MicrosoftAzureBlobstorage1" policyTemplate="online_v1_basic" policyType="azureblobstorage" shortDescription="" version="">
     <credentialName>MicrosoftAzureBlobstorageCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <accountName>YourStorageAccount</accountName>
     <tenantId/>
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
