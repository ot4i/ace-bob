# Azure OpenAI

## Purpose
Connector-specific rules for Azure OpenAI Request nodes.

## When to use
Use this document when the requested ACE flow includes an Azure OpenAI Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Azure OpenAI Request node

## Required node attributes
### Azure OpenAI Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_azureopenai.msgnode`
- `applicationConnectorType="azureopenai"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Azure OpenAI Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Azure OpenAI Request nodes:

- `displayName="Create chat completion"` `action="CREATE"` `businessObject="ChatCompletion"`
- `displayName="Create embedding"` `action="CREATE"` `businessObject="Embedding"`
- `displayName="Create response"` `action="CREATE"` `businessObject="Response"`
- `displayName="Retrieve response"` `action="RETRIEVE"` `businessObject="Response"`
- `displayName="Delete response"` `action="DELETEALL"` `businessObject="Response"`
- `displayName="Create file"` `action="CREATE"` `businessObject="File"`
- `displayName="Retrieve files"` `action="RETRIEVEALL"` `businessObject="File"`
- `displayName="Retrieve file"` `action="RETRIEVE"` `businessObject="File"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Retrieve input items"` `action="RETRIEVEALL"` `businessObject="InputItem"`
- `displayName="Create vector store"` `action="CREATE"` `businessObject="VectorStore"`
- `displayName="Retrieve vector stores"` `action="RETRIEVEALL"` `businessObject="VectorStore"`
- `displayName="Retrieve vector store"` `action="RETRIEVE"` `businessObject="VectorStore"`
- `displayName="Update vector store"` `action="UPDATEALL"` `businessObject="VectorStore"`
- `displayName="Delete vector store"` `action="DELETEALL"` `businessObject="VectorStore"`
- `displayName="Create vector store file"` `action="CREATE"` `businessObject="VectorStoreFile"`
- `displayName="Retrieve vector store files"` `action="RETRIEVEALL"` `businessObject="VectorStoreFile"`
- `displayName="Retrieve vector store file"` `action="RETRIEVE"` `businessObject="VectorStoreFile"`
- `displayName="Update vector store file"` `action="UPDATEALL"` `businessObject="VectorStoreFile"`
- `displayName="Delete vector store file"` `action="DELETEALL"` `businessObject="VectorStoreFile"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AzureOpenAI1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="AzureOpenAI1" policyTemplate="online_v1_basic_api_key" policyType="azureopenai" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
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
