# Amazon RDS

## Purpose
Connector-specific rules for Amazon RDS Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon RDS Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon RDS Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazonrds.msgnode`
- `applicationConnectorType="amazonrds"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon RDS Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon RDS Request nodes:

- `displayName="Create database instance"` `action="CREATE"` `businessObject="DatabaseInstance"`
- `displayName="Retrieve database instances"` `action="RETRIEVEALL"` `businessObject="DatabaseInstance"`
- `displayName="Update database instance"` `action="UPDATEALL"` `businessObject="DatabaseInstance"`
- `displayName="Delete database instance"` `action="DELETEALL"` `businessObject="DatabaseInstance"`
- `displayName="Start database instance"` `action="STARTDBINSTANCE"` `businessObject="DatabaseInstance"`
- `displayName="Stop database instance"` `action="STOPDBINSTANCE"` `businessObject="DatabaseInstance"`
- `displayName="Reboot database instance"` `action="REBOOTDBINSTANCE"` `businessObject="DatabaseInstance"`
- `displayName="Create database snapshot"` `action="CREATE"` `businessObject="DatabaseSnapshot"`
- `displayName="Retrieve database snapshots"` `action="RETRIEVEALL"` `businessObject="DatabaseSnapshot"`
- `displayName="Delete database snapshot"` `action="DELETEALL"` `businessObject="DatabaseSnapshot"`
- `displayName="Retrieve database clusters"` `action="RETRIEVEALL"` `businessObject="DatabaseCluster"`
- `displayName="Start database cluster"` `action="STARTDBCLUSTER"` `businessObject="DatabaseCluster"`
- `displayName="Stop database cluster"` `action="STOPDBCLUSTER"` `businessObject="DatabaseCluster"`
- `displayName="Reboot database cluster"` `action="REBOOTDBCLUSTER"` `businessObject="DatabaseCluster"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="Tag"`
- `displayName="Add tags"` `action="ADDTAGS"` `businessObject="Tag"`
- `displayName="Remove tags"` `action="REMOVETAGS"` `businessObject="Tag"`
- `displayName="Export to Amazon S3"` `action="STARTEXPORTTASK"` `businessObject="Exports"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonRDS1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonRDS1" policyTemplate="onprem_v1_aws_basic_pki" policyType="amazonrds" shortDescription="" version="">
     <credentialName>AmazonRDSCredential</credentialName>
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
