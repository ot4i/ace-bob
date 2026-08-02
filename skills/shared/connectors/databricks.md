# Databricks

## Purpose
Connector-specific rules for Databricks Request nodes.

## When to use
Use this document when the requested ACE flow includes a Databricks Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Databricks Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_databricks.msgnode`
- `applicationConnectorType="databricks"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Databricks Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Databricks Request nodes:

- `displayName="Download file"` `action="CUSTOM"` `businessObject="Files"`
- `displayName="Upload file"` `action="CUSTOM"` `businessObject="Files"`
- `displayName="Download file (Deprecated)"` `action="CUSTOM"` `businessObject="Files"`
- `displayName="Upload file (Deprecated)"` `action="CUSTOM"` `businessObject="Files"`
- `displayName="Delete file"` `action="DELETE"` `businessObject="Files"`
- `displayName="Retrieve volumes"` `action="RETRIEVEWITHWHERE"` `businessObject="Volumes"`
- `displayName="Retrieve all users"` `action="RETRIEVEWITHWHERE"` `businessObject="Users"`
- `displayName="Start SQL warehouse"` `action="CUSTOM"` `businessObject="Warehouses"`
- `displayName="Stop SQL warehouse"` `action="CUSTOM"` `businessObject="Warehouses"`
- `displayName="Run custom SQL query"` `action="CUSTOM"` `businessObject="customSql"`

For dynamically discovered table objects (`TABLE_{tableName}`), the following operations are available per table:

- `displayName="Create {tableName} record"` `action="CREATE"` `businessObject="TABLE_{tableName}"`
- `displayName="Retrieve {tableName} record"` `action="RETRIEVEWITHWHERE"` `businessObject="TABLE_{tableName}"`
- `displayName="Update {tableName} records"` `action="UPDATE"` `businessObject="TABLE_{tableName}"`
- `displayName="Update or create {tableName} record"` `action="UPSERTWITHWHERE"` `businessObject="TABLE_{tableName}"`
- `displayName="Delete {tableName} records"` `action="DELETE"` `businessObject="TABLE_{tableName}"`
- `displayName="Insert multiple records into {tableName}"` `action="CUSTOM"` `businessObject="TABLE_{tableName}"`

For tables with a primary key, these additional bulk operations are also available:

- `displayName="Update multiple records in {tableName}"` `action="CUSTOM"` `businessObject="TABLE_{tableName}"`
- `displayName="Update or create multiple records in {tableName}"` `action="CUSTOM"` `businessObject="TABLE_{tableName}"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Databricks1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Databricks1" policyTemplate="azure_v1_basic" policyType="databricks" shortDescription="" version="">
        <credentialName>DatabricksCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>azure</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <warehouse/>
        <datasetId/>
        <schema/>
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
