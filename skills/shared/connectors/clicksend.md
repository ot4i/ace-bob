# ClickSend

## Purpose
Connector-specific rules for ClickSend Request nodes.

## When to use
Use this document when the requested ACE flow includes a ClickSend Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- ClickSend Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_clicksend.msgnode`
- `applicationConnectorType="clicksend"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For ClickSend Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for ClickSend Request nodes:

- `displayName="Retrieve account information"` `action="RETRIEVE"` `businessObject="Accounts"`
- `displayName="Retrieve contact lists"` `action="RETRIEVEWITHWHERE"` `businessObject="Contact lists"`
- `displayName="Create contact list"` `action="CREATE"` `businessObject="Contact lists"`
- `displayName="Retrieve contact list by ID"` `action="RETRIEVE"` `businessObject="Contact lists"`
- `displayName="Retrieve contacts by list ID"` `action="RETRIEVEWITHWHERE"` `businessObject="Contacts"`
- `displayName="Create contact in contact list"` `action="CREATE"` `businessObject="Contacts"`
- `displayName="Copy contact to contact list"` `action="CUSTOM"` `businessObject="Contacts"`
- `displayName="Transfer contact to contact list"` `action="CUSTOM"` `businessObject="Contacts"`
- `displayName="Retrieve allowed emails for SMS communication"` `action="RETRIEVEWITHWHERE"` `businessObject="Allowed emails for SMS communication"`
- `displayName="Create allowed email for SMS communication"` `action="CREATE"` `businessObject="Allowed emails for SMS communication"`
- `displayName="Retrieve SMS delivery receipts"` `action="RETRIEVEWITHWHERE"` `businessObject="SMS"`
- `displayName="Cancel scheduled SMS"` `action="UPDATE"` `businessObject="SMS"`
- `displayName="Send SMS message"` `action="CREATE"` `businessObject="SMS"`
- `displayName="Retrieve SMS campaigns"` `action="RETRIEVEWITHWHERE"` `businessObject="SMS campaigns"`
- `displayName="Cancel SMS campaign"` `action="UPDATE"` `businessObject="SMS campaigns"`
- `displayName="Create SMS campaign"` `action="CREATE"` `businessObject="SMS campaigns"`
- `displayName="Send voice message"` `action="CREATE"` `businessObject="Voice messages"`
- `displayName="Retrieve voice message history"` `action="RETRIEVEWITHWHERE"` `businessObject="Voice messages"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:ClickSend1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="ClickSend1" policyTemplate="online_v1_basic" policyType="clicksend" shortDescription="" version="">
        <credentialName>ClickSendCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl>https://rest.clicksend.com/v3</apiUrl>
        <isTlsEnabled>false</isTlsEnabled>
        <endpointUrl/>
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
