# HubSpot Marketing

## Purpose
Connector-specific rules for HubSpot Marketing Request and HubSpot Marketing Input nodes.

## When to use
Use this document when the requested ACE flow includes a HubSpot Marketing Request node or HubSpot Marketing Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- HubSpot Marketing Request node
- HubSpot Marketing Input node

## Required node attributes
### HubSpot Marketing Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_hubspotmarketing.msgnode`
- `applicationConnectorType="hubspotmarketing"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### HubSpot Marketing Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_hubspotmarketing.msgnode`
- `applicationConnectorType="hubspotmarketing"`

## Schema file requirements
For HubSpot Marketing Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for HubSpot Marketing Request nodes:

- `displayName="Create contact"` `action="CREATE"` `businessObject="Contacts"`
- `displayName="Retrieve contacts"` `action="RETRIEVEWITHWHERE"` `businessObject="Contacts"`
- `displayName="Retrieve contact"` `action="RETRIEVE"` `businessObject="Contacts"`
- `displayName="Update contact"` `action="UPDATE"` `businessObject="Contacts"`
- `displayName="Delete contact"` `action="DELETE"` `businessObject="Contacts"`
- `displayName="Retrieve email campaigns"` `action="RETRIEVEWITHWHERE"` `businessObject="Email campaigns"`
- `displayName="Retrieve email campaign"` `action="RETRIEVE"` `businessObject="Email campaigns"`
- `displayName="Retrieve contact lists"` `action="RETRIEVEWITHWHERE"` `businessObject="Contact lists"`
- `displayName="Create contact list"` `action="CREATE"` `businessObject="Contact lists"`
- `displayName="Add contact to contact list"` `action="CUSTOM"` `businessObject="Contact lists"`
- `displayName="Delete contact list"` `action="DELETE"` `businessObject="Contact lists"`
- `displayName="Retrieve contact list"` `action="RETRIEVE"` `businessObject="Contact lists"`
- `displayName="Retrieve contacts in contact list"` `action="RETRIEVEWITHWHERE"` `businessObject="Contacts"`
- `displayName="Create marketing event"` `action="CREATE"` `businessObject="Marketing events"`
- `displayName="Retrieve marketing event"` `action="RETRIEVE"` `businessObject="Marketing events"`
- `displayName="Update marketing event"` `action="UPDATE"` `businessObject="Marketing events"`
- `displayName="Delete marketing event"` `action="DELETE"` `businessObject="Marketing events"`
- `displayName="Record marketing event attendance"` `action="CUSTOM"` `businessObject="Marketing events"`
- `displayName="Search marketing events"` `action="RETRIEVEWITHWHERE"` `businessObject="Marketing events"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:HubSpotMarketing1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="HubSpotMarketing1" policyTemplate="online_v1_basic_bearer" policyType="hubspotmarketing" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_BEARER</authenticationMethod>
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
