# Anaplan

## Purpose
Connector-specific rules for Anaplan Request nodes.

## When to use
Use this document when the requested ACE flow includes an Anaplan Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Anaplan Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_anaplan.msgnode`
- `applicationConnectorType="anaplan"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Anaplan Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Anaplan Request nodes:

- `displayName="Execute action"` `action="EXECUTEACTION"` `businessObject="action"`
- `displayName="Execute process"` `action="EXECUTEPROCESS"` `businessObject="process"`
- `displayName="Execute import data to model"` `action="EXECUTEIMPORT"` `businessObject="importDefinition"`
- `displayName="Execute export"` `action="EXECUTEEXPORT"` `businessObject="exportDefinition"`
- `displayName="Upload file content"` `action="CREATE"` `businessObject="file"`
- `displayName="Download file content"` `action="DOWNLOADFILECONTENT"` `businessObject="file"`
- `displayName="Retrieve cell data for a view"` `action="RETRIEVECELLDATAVIEW"` `businessObject="view"`
- `displayName="Execute large volume read for view"` `action="STARTREADREQUEST"` `businessObject="readRequestForView"`
- `displayName="Download page for view"` `action="DOWNLOADPAGES"` `businessObject="readRequestForView"`
- `displayName="Execute large volume read for list"` `action="STARTREADREQUESTFORLIST"` `businessObject="readRequestForList"`
- `displayName="Download page for list"` `action="DOWNLOADPAGESFORLIST"` `businessObject="readRequestForList"`
- `displayName="Retrieve list item"` `action="RETRIEVEALL"` `businessObject="listItem"`
- `displayName="Create multiple list items"` `action="CREATELISTITEM"` `businessObject="listItem"`
- `displayName="Update multiple list items"` `action="UPDATELISTITEM"` `businessObject="listItem"`
- `displayName="Delete multiple List items"` `action="DELETELISTITEM"` `businessObject="listItem"`
- `displayName="Update cell data"` `action="UPDATECELLDATA"` `businessObject="cellData"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Anaplan1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Anaplan1" policyTemplate="online_v1_basic" policyType="anaplan" shortDescription="" version="">
     <credentialName>AnaplanCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
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
