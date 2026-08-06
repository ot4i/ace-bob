# IBM Food Trust

## Purpose
Connector-specific rules for IBM Food Trust Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Food Trust Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Food Trust Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ift.msgnode`
- `applicationConnectorType="ift"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM Food Trust Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM Food Trust Request nodes:

- `displayName="Update or create purchase order"` `action="CREATE"` `businessObject="purchaseorder"`
- `displayName="Update or create despatch advice"` `action="CREATE"` `businessObject="despatchadvice"`
- `displayName="Update or create receiving advice"` `action="CREATE"` `businessObject="receiveadvice"`
- `displayName="Update or create EPCIS aggregation event"` `action="CREATE"` `businessObject="epcisaggregationevent"`
- `displayName="Update or create basic party registration"` `action="CREATE"` `businessObject="basicpartyregistration"`
- `displayName="Update or create item data notification"` `action="CREATE"` `businessObject="itemdatanotification"`
- `displayName="Update or create EPCIS object event"` `action="CREATE"` `businessObject="epcisobjectevent"`
- `displayName="Update or create EPCIS extension"` `action="CREATE"` `businessObject="epcisextension"`
- `displayName="Update or create certificates"` `action="CREATE"` `businessObject="certificates"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Ift1`.
- This connector uses `applicationType="online"` and `authenticationMethod="BASIC"`. The policy includes an `<endpointUrl>` field pre-populated with the IBM Food Trust sandbox API URL.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Ift1" policyTemplate="online_v1_basic" policyType="ift" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl>https://sandbox.food.ibm.com/ift/api/connector</endpointUrl>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
