# Wufoo

## Purpose
Connector-specific rules for Wufoo Request and Wufoo Input nodes.

## When to use
Use this document when the requested ACE flow includes a Wufoo Request node or Wufoo Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Wufoo Request node
- Wufoo Input node

## Required node attributes
### Wufoo Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_wufoo.msgnode`
- `applicationConnectorType="wufoo"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Wufoo Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_wufoo.msgnode`
- `applicationConnectorType="wufoo"`

## Schema file requirements
For Wufoo Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Wufoo Request nodes:

- `displayName="Create form entry"` `action="CREATE"` `businessObject="FormEntry"`
- `displayName="Retrieve form entries"` `action="RETRIEVEALL"` `businessObject="FormEntry"`
- `displayName="Retrieve forms"` `action="RETRIEVEALL"` `businessObject="Form"`
- `displayName="Retrieve reports"` `action="RETRIEVEALL"` `businessObject="Report"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`

The following combinations are allowed for Wufoo Input nodes:

- `displayName="New form entry"` `action="CREATED"` `businessObject="FormEntry"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Wufoo1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Wufoo1" policyTemplate="online_v1_basic" policyType="wufoo" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <subdomain/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
