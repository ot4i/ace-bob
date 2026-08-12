# Zoho CRM

## Purpose
Connector-specific rules for Zoho CRM Request nodes.

## When to use
Use this document when the requested ACE flow includes a Zoho CRM Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Zoho CRM Request node

## Connector type
Zoho CRM uses the `LoopbackNative` discovery protocol with an OpenAPI spec. Operations are expressed using `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Zoho CRM Request nodes:

- `displayName="Retrieve leads with advanced filters"` `action="retrievewithwhere"` `businessObject="Leads"`
- `displayName="Retrieve leads"` `action="retrievewithwhere"` `businessObject="Leads"`
- `displayName="Create lead"` `action="create"` `businessObject="Leads"`
- `displayName="Retrieve lead conversion options"` `action="retrieve"` `businessObject="Leads"`
- `displayName="Convert lead"` `action="custom"` `businessObject="Leads"`
- `displayName="Retrieve deals with advanced filters"` `action="retrievewithwhere"` `businessObject="Deals"`
- `displayName="Retrieve deals"` `action="retrievewithwhere"` `businessObject="Deals"`
- `displayName="Create deal"` `action="create"` `businessObject="Deals"`
- `displayName="Retrieve contacts with advanced filters"` `action="retrievewithwhere"` `businessObject="Contacts"`
- `displayName="Retrieve contacts"` `action="retrievewithwhere"` `businessObject="Contacts"`
- `displayName="Create contact"` `action="create"` `businessObject="Contacts"`
- `displayName="Retrieve accounts with advanced filters"` `action="retrievewithwhere"` `businessObject="Accounts"`
- `displayName="Retrieve accounts"` `action="retrievewithwhere"` `businessObject="Accounts"`
- `displayName="Create account"` `action="create"` `businessObject="Accounts"`
- `displayName="Retrieve campaigns with advanced filters"` `action="retrievewithwhere"` `businessObject="Campaigns"`
- `displayName="Retrieve campaigns"` `action="retrievewithwhere"` `businessObject="Campaigns"`
- `displayName="Create campaign"` `action="create"` `businessObject="Campaigns"`
- `displayName="Retrieve organization"` `action="retrievewithwhere"` `businessObject="Organization"`
- `displayName="Retrieve users"` `action="retrievewithwhere"` `businessObject="Users"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Zohocrm1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Zohocrm1" policyTemplate="online_v1_basic_oauth" policyType="zohocrm" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <apiUrl>https://www.zohoapis.com/crm/v3</apiUrl>
        <tokenUrl>https://accounts.zoho.com/oauth/v2</tokenUrl>
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
