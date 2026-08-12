# Salesloft

## Purpose
Connector-specific rules for Salesloft Request nodes.

## When to use
Use this document when the requested ACE flow includes a Salesloft Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Salesloft Request node

## Connector type
Salesloft is a **dynamic (OpenAPI-based)** connector. It does not use the legacy `xmi:type` / `applicationConnectorType` attributes. The connector is implemented in [`appconnect-connector-salesloft`](../appconnect-connector-salesloft/) and exposes its operations via the OpenAPI specification at [`lib/openapi/connector.json`](../appconnect-connector-salesloft/lib/openapi/connector.json).

## Schema file requirements
For Salesloft Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Salesloft Request nodes:

- `displayName="Retrieve users"` `action="retrievewithwhere"` `businessObject="Users"`
- `displayName="Retrieve user by ID"` `action="retrieve"` `businessObject="Users"`
- `displayName="Update user"` `action="update"` `businessObject="Users"`
- `displayName="Retrieve accounts"` `action="retrievewithwhere"` `businessObject="Accounts"`
- `displayName="Create account"` `action="create"` `businessObject="Accounts"`
- `displayName="Retrieve account by ID"` `action="retrieve"` `businessObject="Accounts"`
- `displayName="Update account"` `action="update"` `businessObject="Accounts"`
- `displayName="Delete account"` `action="delete"` `businessObject="Accounts"`
- `displayName="Retrieve people"` `action="retrievewithwhere"` `businessObject="People"`
- `displayName="Create person"` `action="create"` `businessObject="People"`
- `displayName="Retrieve person by ID"` `action="retrieve"` `businessObject="People"`
- `displayName="Update person"` `action="update"` `businessObject="People"`
- `displayName="Delete person"` `action="delete"` `businessObject="People"`
- `displayName="Retrieve cadences"` `action="retrievewithwhere"` `businessObject="Cadences"`
- `displayName="Retrieve cadence by ID"` `action="retrieve"` `businessObject="Cadences"`
- `displayName="Retrieve cadence memberships"` `action="retrievewithwhere"` `businessObject="Cadence memberships"`
- `displayName="Create cadence membership"` `action="create"` `businessObject="Cadence memberships"`
- `displayName="Retrieve cadence membership by ID"` `action="retrieve"` `businessObject="Cadence memberships"`
- `displayName="Delete cadence membership"` `action="delete"` `businessObject="Cadence memberships"`
- `displayName="Create cadence memberships in bulk"` `action="custom"` `businessObject="Cadence memberships"`
- `displayName="Import cadence"` `action="create"` `businessObject="Cadence imports"`
- `displayName="Export cadence"` `action="retrieve"` `businessObject="Cadence exports"`
- `displayName="Retrieve calls"` `action="retrievewithwhere"` `businessObject="Calls"`
- `displayName="Create call"` `action="create"` `businessObject="Calls"`
- `displayName="Retrieve call by ID"` `action="retrieve"` `businessObject="Calls"`
- `displayName="Retrieve emails"` `action="retrievewithwhere"` `businessObject="Emails"`
- `displayName="Retrieve email by ID"` `action="retrieve"` `businessObject="Emails"`
- `displayName="Retrieve notes"` `action="retrievewithwhere"` `businessObject="Notes"`
- `displayName="Create note"` `action="create"` `businessObject="Notes"`
- `displayName="Retrieve note by ID"` `action="retrieve"` `businessObject="Notes"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Salesloft1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Salesloft1" policyTemplate="online_v1_basic_bearer" policyType="salesloft" shortDescription="" version="">
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
