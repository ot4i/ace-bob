# Yapily

## Purpose
Connector-specific rules for Yapily Request nodes.

## When to use
Use this document when the requested ACE flow includes a Yapily Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Yapily Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_yapily.msgnode`
- `applicationConnectorType="yapily"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Yapily Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Yapily Request nodes:

- `displayName="Retrieve application"` `action="RETRIEVEALL"` `businessObject="self"`
- `displayName="Create user"` `action="CREATE"` `businessObject="user"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="user"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="user"`
- `displayName="Retrieve institutions"` `action="RETRIEVEALL"` `businessObject="institution"`
- `displayName="Retrieve accounts"` `action="RETRIEVEALL"` `businessObject="account"`
- `displayName="Retrieve consents"` `action="RETRIEVEALL"` `businessObject="consent"`
- `displayName="Delete consent"` `action="DELETEALL"` `businessObject="consent"`
- `displayName="Send API key"` `action="SEND_API_KEY"` `businessObject="consent"`
- `displayName="Send access token"` `action="SEND_ACCESS_TOKEN"` `businessObject="consent"`
- `displayName="Exchange one time token"` `action="EXCHANGE_OTT"` `businessObject="consent"`
- `displayName="Retrieve available features for institutions"` `action="RETRIEVEALL"` `businessObject="feature"`
- `displayName="Create account authorization request"` `action="ACCOUNT_AUTH_REQUEST"` `businessObject="authorization"`
- `displayName="Create single payment authorization request"` `action="PAYMENT_AUTH_REQUEST"` `businessObject="authorization"`
- `displayName="Re-authorize consent"` `action="RE_AUTHORIZE"` `businessObject="authorization"`
- `displayName="Create single payment"` `action="CREATE"` `businessObject="payment"`
- `displayName="Retrieve payment status"` `action="RETRIEVEALL"` `businessObject="payment"`
- `displayName="Retrieve account statements"` `action="RETRIEVEALL"` `businessObject="statement"`
- `displayName="Retrieve statement file content"` `action="DOWNLOADFILE"` `businessObject="statement"`
- `displayName="Retrieve transactions"` `action="RETRIEVEALL"` `businessObject="transaction"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Yapily1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Yapily1" policyTemplate="online_v1_basic" policyType="yapily" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
