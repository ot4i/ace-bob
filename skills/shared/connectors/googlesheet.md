# Google Sheets

## Purpose
Connector-specific rules for Google Sheets Input nodes.

## When to use
Use this document when the requested ACE flow includes a Google Sheets Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Sheets Input node

## Note on connector type
This connector is **trigger-only** — it supports event streaming (`EVENT-STREAM`) and provides only an Input node. There is no Google Sheets Request node. The underlying connector name used in the descriptor is `streaming-connector-googlesheet`.

## Required node attributes
### Google Sheets Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_googlesheet.msgnode`
- `applicationConnectorType="googlesheet"`

## Schema file requirements
Google Sheets Input nodes use dynamic schema discovery against the spreadsheet and worksheet hierarchy. No static request or response schema JSON files are created under the `gen` directory for Input nodes.

## Allowed operations
The following combination is allowed for Google Sheets Input nodes:

- `displayName="New spreadsheet row"` `action="CREATED"` `businessObject="worksheetRow"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googlesheet`.
- The policy file is available at `EveryPolicy/googlesheet.policyxml`.
- Note: this connector uses `authenticationMethod="BASIC_OAUTH"`. It also supports `OAUTH2_WEB` authentication.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googlesheet" policyTemplate="online_v1_basic_oauth" policyType="googlesheet" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_OAUTH</authenticationMethod>
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
- [`loopback-connector-googlespreadsheetevent/descriptors/googlespreadsheetevent.json`](../loopback-connector-googlespreadsheetevent/descriptors/googlespreadsheetevent.json)
- [`loopback-connector-googlespreadsheetevent/descriptors/metadata.json`](../loopback-connector-googlespreadsheetevent/descriptors/metadata.json)
- [`loopback-connector-googlespreadsheetevent/lib/googlesheets_constant.json`](../loopback-connector-googlespreadsheetevent/lib/googlesheets_constant.json)
- [`EveryPolicy/googlesheet.policyxml`](../EveryPolicy/googlesheet.policyxml)
