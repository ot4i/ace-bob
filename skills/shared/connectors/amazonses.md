# Amazon SES

## Purpose
Connector-specific rules for Amazon SES Request nodes.

## When to use
Use this document when the requested ACE flow includes an Amazon SES Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Amazon SES Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_amazonses.msgnode`
- `applicationConnectorType="amazonses"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Amazon SES Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Amazon SES Request nodes:

- `displayName="Retrieve configuration sets"` `action="RETRIEVEWITHWHERE"` `businessObject="Configuration sets"`
- `displayName="Retrieve configuration set by name"` `action="RETRIEVE"` `businessObject="Configuration sets"`
- `displayName="Retrieve contact lists"` `action="RETRIEVEWITHWHERE"` `businessObject="Contact lists"`
- `displayName="Retrieve contact list by name"` `action="RETRIEVE"` `businessObject="Contact lists"`
- `displayName="Update contact list information"` `action="UPDATE"` `businessObject="Contact lists"`
- `displayName="Retrieve contacts"` `action="RETRIEVEWITHWHERE"` `businessObject="Contacts"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contacts"`
- `displayName="Retrieve contact by email address"` `action="RETRIEVE"` `businessObject="Contacts"`
- `displayName="Update contact"` `action="UPDATE"` `businessObject="Contacts"`
- `displayName="Delete contact"` `action="DELETE"` `businessObject="Contacts"`
- `displayName="Retrieve email templates"` `action="RETRIEVEWITHWHERE"` `businessObject="Email templates"`
- `displayName="Create email template"` `action="CREATE"` `businessObject="Email templates"`
- `displayName="Retrieve email template by name"` `action="RETRIEVE"` `businessObject="Email templates"`
- `displayName="Delete email template"` `action="DELETE"` `businessObject="Email templates"`
- `displayName="Update email template"` `action="UPDATE"` `businessObject="Email templates"`
- `displayName="Retrieve email identities"` `action="RETRIEVEWITHWHERE"` `businessObject="Email identities"`
- `displayName="Retrieve email identity by email address"` `action="RETRIEVE"` `businessObject="Email identities"`
- `displayName="Delete email identity"` `action="DELETE"` `businessObject="Email identities"`
- `displayName="Send email"` `action="CUSTOM"` `businessObject="Emails"`
- `displayName="Send email using template"` `action="CUSTOM"` `businessObject="Emails"`
- `displayName="Send bulk emails"` `action="CUSTOM"` `businessObject="Emails"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AmazonSES1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="AmazonSES1" policyTemplate="online_v1_aws_basic_pki" policyType="amazonses" shortDescription="" version="">
     <credentialName>AmazonSESCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>AWS_BASIC_PKI</authenticationMethod>
     <region/>
     <oidcServerUrl/>
     <roleArn/>
     <profileArn/>
     <trustAnchorArn/>
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
