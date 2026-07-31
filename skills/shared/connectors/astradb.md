# Astra DB

## Purpose
Connector-specific rules for Astra DB Request nodes.

## When to use
Use this document when the requested ACE flow includes an Astra DB Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Astra DB Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_astradb.msgnode`
- `applicationConnectorType="astradb"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Astra DB Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Astra DB Request nodes:

- `displayName="Retrieve all collections"` `action="GETCOLLECTIONS"` `businessObject="Collections"`
- `displayName="Create document"` `action="CREATEDOCUMENTS"` `businessObject="Documents"`
- `displayName="Create multiple documents"` `action="BULKCREATE"` `businessObject="Documents"`
- `displayName="Retrieve documents"` `action="GETANDOCUMENT"` `businessObject="Documents"`
- `displayName="Update document"` `action="UPDATEDOCUMENT"` `businessObject="Documents"`
- `displayName="Update or create document"` `action="UPSERTDOCUMENT"` `businessObject="Documents"`
- `displayName="Delete document"` `action="DELETEDOCUMENT"` `businessObject="Documents"`
- `displayName="Create multiple rows"` `action="INSERTMULTIPLEROWS"` `businessObject="TABLE <tableName>"`
- `displayName="Create row"` `action="CREATEROW"` `businessObject="TABLE <tableName>"`
- `displayName="Retrieve rows"` `action="GETALLROWS"` `businessObject="TABLE <tableName>"`
- `displayName="Update or create row"` `action="UPDATEROW"` `businessObject="TABLE <tableName>"`
- `displayName="Delete row"` `action="DELETEROW"` `businessObject="TABLE <tableName>"`

Note: Table business objects are discovered dynamically at runtime and take the form `TABLE <tableName>`, where `<tableName>` is the name of a table in the connected Astra DB keyspace.

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AstraDB1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AstraDB1" policyTemplate="online_v1_basic" policyType="astradb" shortDescription="" version="">
     <credentialName>AstraDBCredential</credentialName>
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
