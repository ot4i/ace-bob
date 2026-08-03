# Google Gemini

## Purpose
Connector-specific rules for Google Gemini Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Gemini Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Gemini Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlegemini.msgnode`
- `applicationConnectorType="googlegemini"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Gemini Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Gemini Request nodes:

- `displayName="Generate text with Gemini model"` `action="GENERATETEXT"` `businessObject="Text generation"`
- `displayName="Generate text with custom configuration"` `action="GENERATECONTENT"` `businessObject="Text generation"`
- `displayName="Generate transcript summary"` `action="TRANSCRIPTANALYSIS"` `businessObject="Transcript analysis"`
- `displayName="Analyze document content"` `action="DOCUMENTANALYSIS"` `businessObject="Document analysis"`
- `displayName="Analyze image data"` `action="IMAGEANALYSIS"` `businessObject="Image analysis"`
- `displayName="Generate embeddings"` `action="EMBEDCONTENT"` `businessObject="Text embeddings"`
- `displayName="Generate batch embeddings"` `action="BATCHEMBEDCONTENT"` `businessObject="Text embeddings"`
- `displayName="Count tokens"` `action="COUNTTOKENS"` `businessObject="Token count"`
- `displayName="Translate text"` `action="TRANSLATE"` `businessObject="Translation"`
- `displayName="Retrieve all models"` `action="RETRIEVEALL"` `businessObject="Models"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googlegemini`.
- The policy file is available at `EveryPolicy/googlegemini.policyxml`.
- Note: this connector uses `authenticationMethod="BASIC_API_KEY"` with an API key credential, and includes an `<apiUrl>` field. It does not use OAuth.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googlegemini" policyTemplate="online_v1_basic_api_key" policyType="googlegemini" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_API_KEY</authenticationMethod>
     <apiUrl>https://generativelanguage.googleapis.com</apiUrl>
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
- [`appconnect-connector-googlegemini/descriptors/googlegemini.json`](../appconnect-connector-googlegemini/descriptors/googlegemini.json)
- [`appconnect-connector-googlegemini/descriptors/googlegemini.yaml`](../appconnect-connector-googlegemini/descriptors/googlegemini.yaml)
- [`appconnect-connector-googlegemini/lib/openapi/connector.json`](../appconnect-connector-googlegemini/lib/openapi/connector.json)
- [`EveryPolicy/googlegemini.policyxml`](../EveryPolicy/googlegemini.policyxml)
