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
### Microsoft Azure Blob Storage Request
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

- `displayName="Retrieve blobs"` `action="RETRIEVEALL"` `businessObject="Blob"`
- `displayName="Update or create blob"` `action="UPSERTWITHWHERE"` `businessObject="Blob"`
- `displayName="Delete blob"` `action="DELETEALL"` `businessObject="Blob"`
- `displayName="Abort copy blob"` `action="ABORTCOPYBLOB"` `businessObject="Blob"`
- `displayName="Check blob exists"` `action="CHECKBLOBEXISTS"` `businessObject="Blob"`
- `displayName="Copy blob"` `action="COPYBLOB"` `businessObject="Blob"`
- `displayName="Download blob content"` `action="DOWNLOADBLOBCONTENT"` `businessObject="Blob"`
- `displayName="Set blob metadata"` `action="SETBLOBMETADATA"` `businessObject="Blob"`
- `displayName="Update or create append blob"` `action="UPSERTWITHWHERE"` `businessObject="AppendBlob"`
- `displayName="Append block"` `action="APPENDBLOCK"` `businessObject="AppendBlob"`
- `displayName="Update or create page blob"` `action="UPSERTWITHWHERE"` `businessObject="PageBlob"`
- `displayName="Add page"` `action="ADDPAGE"` `businessObject="PageBlob"`
- `displayName="Create container"` `action="CREATE"` `businessObject="Container"`
- `displayName="Retrieve containers"` `action="RETRIEVEALL"` `businessObject="Container"`
- `displayName="Delete container"` `action="DELETEALL"` `businessObject="Container"`
- `displayName="Check container exists"` `action="CHECKCONTAINEREXISTS"` `businessObject="Container"`
- `displayName="Get container ACL"` `action="GETCONTAINERACL"` `businessObject="Container"`
- `displayName="Set container ACL"` `action="SETCONTAINERACL"` `businessObject="Container"`
- `displayName="Set container metadata"` `action="SETCONTAINERMETADATA"` `businessObject="Container"`
- `displayName="Create snapshot"` `action="CREATE"` `businessObject="Snapshot"`
- `displayName="Retrieve snapshots"` `action="RETRIEVEALL"` `businessObject="Snapshot"`
- `displayName="Delete snapshot"` `action="DELETEALL"` `businessObject="Snapshot"`
- `displayName="Retrieve versions"` `action="RETRIEVEALL"` `businessObject="Version"`
- `displayName="Delete version"` `action="DELETEALL"` `businessObject="Version"`
- `displayName="Get blob service properties"` `action="GETBLOBSERVICEPROPERTIES"` `businessObject="BlobService"`
- `displayName="Set blob service properties"` `action="SETBLOBSERVICEPROPERTIES"` `businessObject="BlobService"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AzureBlobStorage1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="AzureBlobStorage1" policyTemplate="online_v1_basic" policyType="azureblobstorage" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <accountName/>
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
