# Twilio

## Purpose
Connector-specific rules for Twilio Request nodes.

## When to use
Use this document when the requested ACE flow includes a Twilio Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Twilio Request node

## Required node attributes
### Twilio Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_twilio.msgnode`
- `applicationConnectorType="twilio"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Twilio Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Twilio Request nodes:

- `displayName="Create message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Retrieve message"` `action="RETRIEVE"` `businessObject="Message"`
- `displayName="Redact message"` `action="REDACTMESSAGE"` `businessObject="Message"`
- `displayName="Cancel scheduled message"` `action="CANCELSCHEDULEDMESSAGE"` `businessObject="Message"`
- `displayName="Create call"` `action="CREATE"` `businessObject="Call"`
- `displayName="Retrieve calls"` `action="RETRIEVEALL"` `businessObject="Call"`
- `displayName="Retrieve call"` `action="RETRIEVE"` `businessObject="Call"`
- `displayName="Retrieve incoming phone numbers"` `action="RETRIEVEALL"` `businessObject="IncomingPhoneNumber"`
- `displayName="Retrieve incoming phone number"` `action="RETRIEVE"` `businessObject="IncomingPhoneNumber"`
- `displayName="Retrieve message services"` `action="RETRIEVEALL"` `businessObject="MessageService"`
- `displayName="Retrieve message service"` `action="RETRIEVE"` `businessObject="MessageService"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Twilio1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Twilio1" policyTemplate="online_v1_basic" policyType="twilio" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
