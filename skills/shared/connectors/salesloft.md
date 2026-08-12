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

- `summary="Retrieve users"` `action="retrievewithwhere"` `model="Users"`
- `summary="Retrieve user by ID"` `action="retrieve"` `model="Users"`
- `summary="Update user"` `action="update"` `model="Users"`
- `summary="Retrieve accounts"` `action="retrievewithwhere"` `model="Accounts"`
- `summary="Create account"` `action="create"` `model="Accounts"`
- `summary="Retrieve account by ID"` `action="retrieve"` `model="Accounts"`
- `summary="Update account"` `action="update"` `model="Accounts"`
- `summary="Delete account"` `action="delete"` `model="Accounts"`
- `summary="Retrieve people"` `action="retrievewithwhere"` `model="People"`
- `summary="Create person"` `action="create"` `model="People"`
- `summary="Retrieve person by ID"` `action="retrieve"` `model="People"`
- `summary="Update person"` `action="update"` `model="People"`
- `summary="Delete person"` `action="delete"` `model="People"`
- `summary="Retrieve cadences"` `action="retrievewithwhere"` `model="Cadences"`
- `summary="Retrieve cadence by ID"` `action="retrieve"` `model="Cadences"`
- `summary="Retrieve cadence memberships"` `action="retrievewithwhere"` `model="Cadence memberships"`
- `summary="Create cadence membership"` `action="create"` `model="Cadence memberships"`
- `summary="Retrieve cadence membership by ID"` `action="retrieve"` `model="Cadence memberships"`
- `summary="Delete cadence membership"` `action="delete"` `model="Cadence memberships"`
- `summary="Create cadence memberships in bulk"` `action="custom"` `model="Cadence memberships"`
- `summary="Import cadence"` `action="create"` `model="Cadence imports"`
- `summary="Export cadence"` `action="retrieve"` `model="Cadence exports"`
- `summary="Retrieve calls"` `action="retrievewithwhere"` `model="Calls"`
- `summary="Create call"` `action="create"` `model="Calls"`
- `summary="Retrieve call by ID"` `action="retrieve"` `model="Calls"`
- `summary="Retrieve emails"` `action="retrievewithwhere"` `model="Emails"`
- `summary="Retrieve email by ID"` `action="retrieve"` `model="Emails"`
- `summary="Retrieve notes"` `action="retrievewithwhere"` `model="Notes"`
- `summary="Create note"` `action="create"` `model="Notes"`
- `summary="Retrieve note by ID"` `action="retrieve"` `model="Notes"`

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
