# Salesforce Account Engagement

## Purpose
Connector-specific rules for Salesforce Account Engagement Request nodes.

## When to use
Use this document when the requested ACE flow includes a Salesforce Account Engagement Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Salesforce Account Engagement Request node

## Connector type
Salesforce Account Engagement uses the `LoopbackNative` discovery protocol with an OpenAPI specification. Operations are resolved at runtime from the OpenAPI specification. Use the `summary`, `action`, and `model` attributes on the node.

## Required node attributes
### Salesforce Account Engagement Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_salesforceae.msgnode`
- `applicationConnectorType="salesforceae"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Salesforce Account Engagement Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Salesforce Account Engagement Request nodes:

- `displayName="Retrieve prospects"` `action="retrievewithwhere"` `businessObject="Prospects"`
- `displayName="Create prospect"` `action="create"` `businessObject="Prospects"`
- `displayName="Update prospect"` `action="update"` `businessObject="Prospects"`
- `displayName="Delete prospect"` `action="delete"` `businessObject="Prospects"`
- `displayName="Retrieve visitors"` `action="retrievewithwhere"` `businessObject="Visitors"`
- `displayName="Assign visitor to prospect"` `action="custom"` `businessObject="Visitors"`
- `displayName="Retrieve users"` `action="retrievewithwhere"` `businessObject="Users"`
- `displayName="Retrieve lists"` `action="retrievewithwhere"` `businessObject="Lists"`
- `displayName="Create list"` `action="create"` `businessObject="Lists"`
- `displayName="Update list"` `action="update"` `businessObject="Lists"`
- `displayName="Delete list"` `action="delete"` `businessObject="Lists"`
- `displayName="Retrieve list memberships"` `action="retrievewithwhere"` `businessObject="List memberships"`
- `displayName="Create list membership"` `action="create"` `businessObject="List memberships"`
- `displayName="Update list membership"` `action="update"` `businessObject="List memberships"`
- `displayName="Delete list membership"` `action="delete"` `businessObject="List memberships"`
- `displayName="Retrieve visits"` `action="retrievewithwhere"` `businessObject="Visits"`
- `displayName="Retrieve campaigns"` `action="retrievewithwhere"` `businessObject="Campaigns"`
- `displayName="Create campaign"` `action="create"` `businessObject="Campaigns"`
- `displayName="Update campaign"` `action="update"` `businessObject="Campaigns"`
- `displayName="Retrieve folders"` `action="retrievewithwhere"` `businessObject="Folders"`
- `displayName="Retrieve emails"` `action="retrievewithwhere"` `businessObject="Emails"`
- `displayName="Send email using template"` `action="create"` `businessObject="Emails"`
- `displayName="Send email"` `action="create"` `businessObject="Emails"`
- `displayName="Retrieve email templates"` `action="retrievewithwhere"` `businessObject="Email templates"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Salesforceae1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Salesforceae1" policyTemplate="online_v1_basic_oauth" policyType="salesforceae" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <endpointUrl/>
        <instanceId/>
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
