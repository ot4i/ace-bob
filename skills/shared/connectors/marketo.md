# Marketo

## Purpose
Connector-specific rules for Marketo Request and Marketo Input nodes.

## When to use
Use this document when the requested ACE flow includes a Marketo Request node or Marketo Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Marketo Request node
- Marketo Input node

## Required node attributes
### Marketo Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_marketo.msgnode`
- `applicationConnectorType="marketo"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Marketo Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_marketo.msgnode`
- `applicationConnectorType="marketo"`

## Schema file requirements
For Marketo Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Marketo Request nodes:

- `displayName="Create lead"` `action="CREATE"` `businessObject="Lead"`
- `displayName="Retrieve lead"` `action="RETRIEVE"` `businessObject="Lead"`
- `displayName="Update or create lead"` `action="UPSERTWITHWHERE"` `businessObject="Lead"`
- `displayName="Delete lead"` `action="DELETEALL"` `businessObject="Lead"`
- `displayName="Create opportunity"` `action="CREATE"` `businessObject="Opportunity"`
- `displayName="Retrieve opportunity"` `action="RETRIEVE"` `businessObject="Opportunity"`
- `displayName="Update or create opportunity"` `action="UPSERTWITHWHERE"` `businessObject="Opportunity"`
- `displayName="Delete opportunity"` `action="DELETEALL"` `businessObject="Opportunity"`
- `displayName="Retrieve lists"` `action="RETRIEVEALL"` `businessObject="List"`
- `displayName="Retrieve list"` `action="RETRIEVE"` `businessObject="List"`
- `displayName="Add lead to list"` `action="ADDLEADTOLIST"` `businessObject="List"`
- `displayName="Retrieve campaigns"` `action="RETRIEVEALL"` `businessObject="Campaign"`
- `displayName="Schedule campaign"` `action="SCHEDULECAMPAIGN"` `businessObject="ScheduleCampaign"`

The following combination is allowed for Marketo Input nodes:

- `displayName="New lead"` `action="CREATED"` `businessObject="Lead"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Marketo1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Marketo1" policyTemplate="online_v1_oauth2_credentials" policyType="marketo" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_CREDENTIALS</authenticationMethod>
        <identityUrl/>
        <apiUrl/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
