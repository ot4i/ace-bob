# Google BigQuery

## Purpose
Connector-specific rules for Google BigQuery Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google BigQuery Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google BigQuery Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlebigquery.msgnode`
- `applicationConnectorType="googlebigquery"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google BigQuery Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Google BigQuery Request nodes:

- `displayName="Retrieve tables"` `action="RETRIEVEALL"` `businessObject="Table"`
- `displayName="Update table"` `action="UPDATEALL"` `businessObject="Table"`
- `displayName="Delete table"` `action="DELETEALL"` `businessObject="Table"`
- `displayName="Restore deleted table"` `action="RESTOREDELETEDTABLE"` `businessObject="Table"`
- `displayName="Copy table"` `action="COPYTABLE"` `businessObject="Table"`
- `displayName="Export data"` `action="EXPORTDATA"` `businessObject="Table"`
- `displayName="Load data"` `action="LOADDATA"` `businessObject="Table"`
- `displayName="Retrieve views"` `action="RETRIEVEALL"` `businessObject="View"`
- `displayName="Delete view"` `action="DELETEALL"` `businessObject="View"`
- `displayName="Create dataset"` `action="CREATE"` `businessObject="Dataset"`
- `displayName="Retrieve datasets"` `action="RETRIEVEALL"` `businessObject="Dataset"`
- `displayName="Update dataset"` `action="UPDATEALL"` `businessObject="Dataset"`
- `displayName="Delete dataset"` `action="DELETEALL"` `businessObject="Dataset"`
- `displayName="Retrieve jobs"` `action="RETRIEVEALL"` `businessObject="Job"`
- `displayName="Execute custom SQL"` `action="EXECUTECUSTOMSQL"` `businessObject="Sql"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googlebigquery`.
- The policy file is available at `EveryPolicy/googlebigquery.policyxml`.
- Note: this connector uses `authenticationMethod="BASIC"` with service account credentials (client email and private key) rather than OAuth. The policy also requires `<projectId/>` and `<datasetId/>` fields.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googlebigquery" policyTemplate="online_v1_basic" policyType="googlebigquery" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <projectId/>
     <datasetId/>
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
- [`loopback-connector-googlebigquery/descriptors/googlebigquery.json`](../loopback-connector-googlebigquery/descriptors/googlebigquery.json)
- [`loopback-connector-googlebigquery/descriptors/googlebigquery.yaml`](../loopback-connector-googlebigquery/descriptors/googlebigquery.yaml)
- [`loopback-connector-googlebigquery/lib/models/objects.json`](../loopback-connector-googlebigquery/lib/models/objects.json)
- [`loopback-connector-googlebigquery/lib/models/table.json`](../loopback-connector-googlebigquery/lib/models/table.json)
- [`loopback-connector-googlebigquery/lib/models/view.json`](../loopback-connector-googlebigquery/lib/models/view.json)
- [`loopback-connector-googlebigquery/lib/models/dataset.json`](../loopback-connector-googlebigquery/lib/models/dataset.json)
- [`loopback-connector-googlebigquery/lib/models/job.json`](../loopback-connector-googlebigquery/lib/models/job.json)
- [`loopback-connector-googlebigquery/lib/models/sql.json`](../loopback-connector-googlebigquery/lib/models/sql.json)
- [`loopback-connector-googlebigquery/lib/models/project.json`](../loopback-connector-googlebigquery/lib/models/project.json)
- [`loopback-connector-googlebigquery/lib/googlebigqueryConstants.json`](../loopback-connector-googlebigquery/lib/googlebigqueryConstants.json)
- [`EveryPolicy/googlebigquery.policyxml`](../EveryPolicy/googlebigquery.policyxml)
