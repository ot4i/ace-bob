# Infobip

## Purpose
Connector-specific rules for Infobip Request nodes.

## When to use
Use this document when the requested ACE flow includes an Infobip Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Infobip Request node

## Required node attributes
### Infobip Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_infobip.msgnode`
- `applicationConnectorType="infobip"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Infobip Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Infobip Request nodes:

- `displayName="Retrieve WhatsApp templates by sender number"` `action="RETRIEVEWITHWHERE"` `businessObject="WhatsApp"`
- `displayName="Send WhatsApp template message"` `action="CREATE"` `businessObject="WhatsApp"`
- `displayName="Retrieve entities"` `action="RETRIEVEWITHWHERE"` `businessObject="Entities"`
- `displayName="Create entity"` `action="CREATE"` `businessObject="Entities"`
- `displayName="Send single voice message"` `action="CREATE"` `businessObject="Voice"`
- `displayName="Send SMS message"` `action="CREATE"` `businessObject="SMS"`
- `displayName="Retrieve account balance"` `action="RETRIEVE"` `businessObject="Account management"`
- `displayName="Retrieve free messages count"` `action="RETRIEVE"` `businessObject="Account management"`
- `displayName="Retrieve all accounts"` `action="RETRIEVEWITHWHERE"` `businessObject="Account management"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Infobip1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Infobip1" policyTemplate="online_v1_basic" policyType="infobip" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
        <isTlsEnabled>false</isTlsEnabled>
        <endpointUrl/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
