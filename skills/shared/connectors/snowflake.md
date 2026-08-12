# Snowflake

## Purpose
Connector-specific rules for Snowflake Request nodes.

## When to use
Use this document when the requested ACE flow includes a Snowflake Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Snowflake Request node

## Required node attributes
### Snowflake Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_snowflake.msgnode`
- `applicationConnectorType="snowflake"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Snowflake Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Snowflake Request nodes:

- `displayName="Create pipe"` `action="CREATE"` `businessObject="Pipe"`
- `displayName="Retrieve pipes"` `action="RETRIEVEALL"` `businessObject="Pipe"`
- `displayName="Create row"` `action="CREATE"` `businessObject="Row"`
- `displayName="Retrieve rows"` `action="RETRIEVEALL"` `businessObject="Row"`
- `displayName="Update rows"` `action="UPDATEALL"` `businessObject="Row"`
- `displayName="Delete rows"` `action="DELETEALL"` `businessObject="Row"`
- `displayName="Create stage"` `action="CREATE"` `businessObject="Stage"`
- `displayName="Retrieve stages"` `action="RETRIEVEALL"` `businessObject="Stage"`
- `displayName="Create stored procedure"` `action="CREATE"` `businessObject="StoredProcedure"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Task"`
- `displayName="Copy into table"` `action="COPYINTOTABLE"` `businessObject="Table"`
- `displayName="Copy into table with transformation"` `action="COPYINTOTABLEWITHTRANSFORMATION"` `businessObject="Table"`
- `displayName="Copy from table into location"` `action="COPYFROMTABLE"` `businessObject="Table"`
- `displayName="Execute custom SQL"` `action="EXECUTECUSTOMSQL"` `businessObject="CustomSQLQuery"`
- `displayName="Call procedure"` `action="CALLPROCEDURE"` `businessObject="StoredProcedure"`
- `displayName="Alter task"` `action="ALTERTASK"` `businessObject="Task"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Snowflake1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Snowflake1" policyTemplate="online_v1_basic" policyType="snowflake" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <hostname/>
        <database/>
        <schema/>
        <warehouse/>
        <role/>
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
