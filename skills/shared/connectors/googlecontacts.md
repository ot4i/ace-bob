# Google Contacts

## Purpose
Connector-specific rules for Google Contacts Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Contacts Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Contacts Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlecontacts.msgnode`
- `applicationConnectorType="googlecontacts"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Contacts Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Contacts Request nodes:

- `displayName="Create contact group"` `action="CREATE"` `businessObject="Contact groups"`
- `displayName="Retrieve contact groups"` `action="RETRIEVEALL"` `businessObject="Contact groups"`
- `displayName="Retrieve contact group by ID"` `action="RETRIEVE"` `businessObject="Contact groups"`
- `displayName="Update contact group"` `action="UPDATEALL"` `businessObject="Contact groups"`
- `displayName="Delete contact group"` `action="DELETEALL"` `businessObject="Contact groups"`
- `displayName="Add contacts to contact group"` `action="ADDCONTACTSTOCONTACTGROUP"` `businessObject="Contact groups"`
- `displayName="Remove contacts from contact group"` `action="REMOVECONTACTSFROMCONTACTGROUP"` `businessObject="Contact groups"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contacts"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contacts"`
- `displayName="Retrieve contact by ID"` `action="RETRIEVE"` `businessObject="Contacts"`
- `displayName="Retrieve contacts by search string"` `action="SEARCHCONTACTS"` `businessObject="Contacts"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contacts"`
- `displayName="Update contact photo"` `action="UPDATECONTACTPHOTO"` `businessObject="Contacts"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contacts"`
- `displayName="Delete contact photo"` `action="DELETECONTACTPHOTO"` `businessObject="Contacts"`
- `displayName="Refresh contacts cache"` `action="REFRESHCONTACTSCACHE"` `businessObject="Contacts"`
- `displayName="Retrieve other contacts"` `action="RETRIEVEALL"` `businessObject="Other contacts"`
- `displayName="Retrieve other contacts by search string"` `action="SEARCHOTHERCONTACTS"` `businessObject="Other contacts"`
- `displayName="Refresh other contacts cache"` `action="REFRESHOTHERCONTACTSCACHE"` `businessObject="Other contacts"`
- `displayName="Copy to my contacts"` `action="COPYTOMYCONTACTS"` `businessObject="Other contacts"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Googlecontacts1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Googlecontacts1" policyTemplate="online_v1_basic_oauth" policyType="googlecontacts" shortDescription="" version="">
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