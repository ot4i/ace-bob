# Salesforce Marketing Cloud

## Purpose
Connector-specific rules for Salesforce Marketing Cloud Request nodes.

## When to use
Use this document when the requested ACE flow includes a Salesforce Marketing Cloud Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Salesforce Marketing Cloud Request node

## Required node attributes
### Salesforce Marketing Cloud Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_salesforcemc.msgnode`
- `applicationConnectorType="salesforcemc"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Salesforce Marketing Cloud Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Salesforce Marketing Cloud Request nodes:

- `displayName="Create category"` `action="CREATE"` `businessObject="Category"`
- `displayName="Retrieve categories"` `action="RETRIEVEALL"` `businessObject="Category"`
- `displayName="Update category"` `action="UPDATEALL"` `businessObject="Category"`
- `displayName="Delete category"` `action="DELETEALL"` `businessObject="Category"`
- `displayName="Create location"` `action="CREATE"` `businessObject="Location"`
- `displayName="Retrieve locations"` `action="RETRIEVEALL"` `businessObject="Location"`
- `displayName="Update location"` `action="UPDATEALL"` `businessObject="Location"`
- `displayName="Delete location"` `action="DELETEALL"` `businessObject="Location"`
- `displayName="Create campaign"` `action="CREATE"` `businessObject="Campaign"`
- `displayName="Retrieve campaigns"` `action="RETRIEVEALL"` `businessObject="Campaign"`
- `displayName="Delete campaign"` `action="DELETEALL"` `businessObject="Campaign"`
- `displayName="Associate asset with campaign"` `action="ASSOCIATEASSETTOCAMPAIGN"` `businessObject="Campaign"`
- `displayName="Disassociate asset from campaign"` `action="UNASSOCIATEASSETFROMCAMPAIGN"` `businessObject="Campaign"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contact"`
- `displayName="Delete contacts"` `action="DELETECONTACTS"` `businessObject="Contact"`
- `displayName="Check deleted contact status"` `action="CHECKDELETECONTACTSTATUS"` `businessObject="Contact"`
- `displayName="Create event definition"` `action="CREATE"` `businessObject="EventDefinition"`
- `displayName="Retrieve event definitions"` `action="RETRIEVEALL"` `businessObject="EventDefinition"`
- `displayName="Update event definition"` `action="UPDATEALL"` `businessObject="EventDefinition"`
- `displayName="Delete event definition"` `action="DELETEALL"` `businessObject="EventDefinition"`
- `displayName="Create journey"` `action="CREATE"` `businessObject="Journey"`
- `displayName="Retrieve journeys"` `action="RETRIEVEALL"` `businessObject="Journey"`
- `displayName="Delete journey"` `action="DELETEALL"` `businessObject="Journey"`
- `displayName="Stop journey"` `action="STOPJOURNEY"` `businessObject="Journey"`
- `displayName="Publish journey"` `action="PUBLISHJOURNEY"` `businessObject="Journey"`
- `displayName="Get publish journey status"` `action="GETPUBLISHJOURNEYSTATUS"` `businessObject="Journey"`
- `displayName="Pause journey"` `action="PAUSEJOURNEY"` `businessObject="Journey"`
- `displayName="Resume journey"` `action="RESUMEJOURNEY"` `businessObject="Journey"`
- `displayName="Create data extension"` `action="CREATE"` `businessObject="DataExtension"`
- `displayName="Retrieve data extensions"` `action="RETRIEVEALL"` `businessObject="DataExtension"`
- `displayName="Update data extension"` `action="UPDATEALL"` `businessObject="DataExtension"`
- `displayName="Delete data extension"` `action="DELETEALL"` `businessObject="DataExtension"`
- `displayName="Retrieve assets"` `action="RETRIEVEALL"` `businessObject="Asset"`
- `displayName="Create data extension value"` `action="CREATE"` `businessObject="DataExtensionValue"`
- `displayName="Retrieve data extension values"` `action="RETRIEVEALL"` `businessObject="DataExtensionValue"`
- `displayName="Update data extension value"` `action="UPDATEALL"` `businessObject="DataExtensionValue"`
- `displayName="Delete data extension value"` `action="DELETEALL"` `businessObject="DataExtensionValue"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Salesforcemc1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Salesforcemc1" policyTemplate="enhanced_v1_basic_oauth" policyType="salesforcemc" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>enhanced</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <subdomain/>
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
