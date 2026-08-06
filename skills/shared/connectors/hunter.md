# Hunter

## Purpose
Connector-specific rules for Hunter Request and Hunter Input nodes.

## When to use
Use this document when the requested ACE flow includes a Hunter Request node or Hunter Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Hunter Request node
- Hunter Input node

## Required node attributes
### Hunter Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_hunter.msgnode`
- `applicationConnectorType="hunter"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Hunter Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_hunter.msgnode`
- `applicationConnectorType="hunter"`

## Schema file requirements
For Hunter Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Hunter Request nodes:

- `displayName="Create lead"` `action="CREATE"` `businessObject="Leads"`
- `displayName="Retrieve all leads"` `action="RETRIEVEWITHWHERE"` `businessObject="Leads"`
- `displayName="Retrieve lead by ID"` `action="RETRIEVE"` `businessObject="Leads"`
- `displayName="Update lead"` `action="UPDATE"` `businessObject="Leads"`
- `displayName="Update or create lead"` `action="UPSERTWITHWHERE"` `businessObject="Leads"`
- `displayName="Delete lead"` `action="DELETE"` `businessObject="Leads"`
- `displayName="Create leads list"` `action="CREATE"` `businessObject="Leads lists"`
- `displayName="Retrieve all leads lists"` `action="RETRIEVEWITHWHERE"` `businessObject="Leads lists"`
- `displayName="Retrieve leads list by ID"` `action="RETRIEVE"` `businessObject="Leads lists"`
- `displayName="Update leads list"` `action="UPDATE"` `businessObject="Leads lists"`
- `displayName="Delete leads list"` `action="DELETE"` `businessObject="Leads lists"`
- `displayName="Retrieve all campaigns"` `action="RETRIEVEWITHWHERE"` `businessObject="Campaigns"`
- `displayName="Retrieve recipients of a campaign"` `action="RETRIEVEWITHWHERE"` `businessObject="Campaigns"`
- `displayName="Add recipient to a campaign"` `action="CREATE"` `businessObject="Campaigns"`
- `displayName="Cancel scheduled emails to recipient from a campaign"` `action="DELETE"` `businessObject="Campaigns"`
- `displayName="Find email"` `action="RETRIEVE"` `businessObject="Emails"`
- `displayName="Search email addresses by domain"` `action="RETRIEVEWITHWHERE"` `businessObject="Domains"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Hunter1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Hunter1" policyTemplate="online_v1_basic_api_key" policyType="hunter" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <apiUrl>https://api.hunter.io</apiUrl>
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
