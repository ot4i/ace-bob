# Microsoft Excel Online

## Purpose
Connector-specific rules for Microsoft Excel Online Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Excel Online Request node or Microsoft Excel Online Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Excel Online Request node
- Microsoft Excel Online Input node

## Required node attributes
### Microsoft Excel Online Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msexcel.msgnode`
- `applicationConnectorType="msexcel"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Microsoft Excel Online Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_msexcel.msgnode`
- `applicationConnectorType="msexcel"`

## Schema file requirements
For Microsoft Excel Online Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Excel Online Request nodes:

- `displayName="Insert row"` `action="CREATE"` `businessObject="Row"`
- `displayName="Retrieve rows"` `action="RETRIEVEALL"` `businessObject="Row"`
- `displayName="Delete row"` `action="DELETEALL"` `businessObject="Row"`
- `displayName="Update row"` `action="UPDATEALL"` `businessObject="Row"`
- `displayName="Append row"` `action="APPENDROW"` `businessObject="Row"`
- `displayName="New row appended"` `action="CREATED"` `businessObject="Row"`
- `displayName="Retrieve drives"` `action="RETRIEVEALL"` `businessObject="Drive"`
- `displayName="Create workbook"` `action="CREATE"` `businessObject="Workbook"`
- `displayName="Retrieve workbooks"` `action="RETRIEVEALL"` `businessObject="Workbook"`
- `displayName="Delete workbook"` `action="DELETEALL"` `businessObject="Workbook"`
- `displayName="Rename workbook"` `action="UPDATEALL"` `businessObject="Workbook"`
- `displayName="Download workbook"` `action="DOWNLOADWORKBOOK"` `businessObject="Workbook"`
- `displayName="Upload workbook"` `action="UPLOADWORKBOOK"` `businessObject="Workbook"`
- `displayName="Create worksheet"` `action="CREATE"` `businessObject="Worksheet"`
- `displayName="Retrieve worksheets"` `action="RETRIEVEALL"` `businessObject="Worksheet"`
- `displayName="Delete worksheet"` `action="DELETEALL"` `businessObject="Worksheet"`
- `displayName="Rename worksheet"` `action="UPDATEALL"` `businessObject="Worksheet"`
- `displayName="Create table"` `action="CREATE"` `businessObject="Table"`
- `displayName="Retrieve tables"` `action="RETRIEVEALL"` `businessObject="Table"`
- `displayName="Delete table"` `action="DELETEALL"` `businessObject="Table"`
- `displayName="Update table"` `action="UPDATEALL"` `businessObject="Table"`
- `displayName="Retrieve column data"` `action="RETRIEVEALL"` `businessObject="Column"`
- `displayName="Append table row"` `action="CREATE"` `businessObject="Tablerow"`
- `displayName="Retrieve table rows"` `action="RETRIEVEALL"` `businessObject="Tablerow"`
- `displayName="Delete table row"` `action="DELETEALL"` `businessObject="Tablerow"`
- `displayName="Update table row"` `action="UPDATEALL"` `businessObject="Tablerow"`
- `displayName="New table row appended"` `action="CREATED"` `businessObject="Tablerow"`
- `displayName="Retrieve cell ranges"` `action="RETRIEVEALL"` `businessObject="Range"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MicrosoftExcelOnline1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="MicrosoftExcelOnline1" policyTemplate="online_v1_basic_oauth" policyType="msexcel" shortDescription="" version="">
     <credentialName>MicrosoftExcelOnlineCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_OAUTH</authenticationMethod>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
