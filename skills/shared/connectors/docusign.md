# Dropbox

## Purpose
Connector-specific rules for DocuSign Request nodes.

## When to use
Use this document when the requested ACE flow includes a DocuSign Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- DocuSign Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_docusign.msgnode`
- `applicationConnectorType="docusign"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For DocuSign Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for DocuSign Request nodes:

- `displayName="Create attachment"` `action="CREATE"` `businessObject="attachment"`
- `displayName="Retrieve attachments"` `action="RETRIEVEALL"` `businessObject="attachment"`
- `displayName="Update attachment"` `action="UPDATE"` `businessObject="attachment"`
- `displayName="Delete attachment"` `action="DELETEALL"` `businessObject="attachment"`
- `displayName="Retrieve documents"` `action="RETRIEVEALL"` `businessObject="document"`
- `displayName="Delete document"` `action="DELETEALL"` `businessObject="document"`
- `displayName="Bulk create or update document"` `action="UPSERTWITHWHERE"` `businessObject="document"`
- `displayName="Retrieve recipients" action="RETRIEVEALL"` `businessObject="recipient"`
- `displayName="Delete recipient"` `action="DELETEALL"` `businessObject="recipient"`
- `displayName="Bulk create or update recipient"` `action="UPSERTWITHWHERE"` `businessObject="recipient"`
- `displayName="Create envelope"` `action="CREATE"` `businessObject="envelope"`
- `displayName="Retrieve envelopes"` `action="RETRIEVEALL"` `businessObject="envelope"`
- `displayName="Update envelope"` `action="UPDATE"` `businessObject="envelope"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Docusign1`.

## Example policy

   **Option A — OAuth (recommended default):** Use policyTemplate="online_v1_basic_oauth" and authenticationMethod="BASIC_OAUTH". The associated credential must have credentialType="docusign", authenticationType="oauth" and requires the following properties: accessToken, clientId, clientSecret, refreshToken.
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="DocuSign1" policyTemplate="online_v1_basic_oauth" policyType="docusign" shortDescription="" version="">
       <credentialName>DocuSignCredential</credentialName>
       <applicationVersion>v1</applicationVersion>
       <applicationType>online</applicationType>
       <authenticationMethod>BASIC_OAUTH</authenticationMethod>
       <endpointUrl>account.docusign.com</endpointUrl>
       <proxyId/>
     </policy>
   </policies>
   ```

   **Option B — API Key:** Use policyTemplate="online_v1_basic_api_key" and authenticationMethod="BASIC_API_KEY". The associated credential must have credentialType="docusign", authenticationType="basicRSA" and requires the following properties: apiKey, privateKey, username.
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="DocuSign1" policyTemplate="online_v1_basic_api_key" policyType="docusign" shortDescription="" version="">
       <credentialName>DocuSignCredential</credentialName>
       <applicationVersion>v1</applicationVersion>
       <applicationType>online</applicationType>
       <authenticationMethod>BASIC_API_KEY</authenticationMethod>
       <endpointUrl>account.docusign.com</endpointUrl>
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
