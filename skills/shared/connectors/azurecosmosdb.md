# Azure Cosmos DB

## Purpose
Connector-specific rules for Azure Cosmos DB Request nodes.

## When to use
Use this document when the requested ACE flow includes an Azure Cosmos DB Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Azure Cosmos DB Request node

## Required node attributes
### Azure Cosmos DB Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_azurecosmosdb.msgnode`
- `applicationConnectorType="azurecosmosdb"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Azure Cosmos DB Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Azure Cosmos DB Request nodes:

- `displayName="Create item"` `action="CREATE"` `businessObject="Item"`
- `displayName="Retrieve items"` `action="RETRIEVEALL"` `businessObject="Item"`
- `displayName="Retrieve item"` `action="RETRIEVE"` `businessObject="Item"`
- `displayName="Update item"` `action="UPDATEALL"` `businessObject="Item"`
- `displayName="Delete item"` `action="DELETEALL"` `businessObject="Item"`
- `displayName="Execute custom SQL"` `action="EXECUTECUSTOMSQL"` `businessObject="CustomSQL"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AzureCosmosDB1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="AzureCosmosDB1" policyTemplate="online_v1_basic" policyType="azurecosmosdb" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
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
