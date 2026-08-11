# Microsoft Entra ID

## Purpose
Connector-specific rules for Microsoft Entra ID Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Entra ID Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Entra ID Request node

## Required node attributes
### Microsoft Entra ID Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_azuread.msgnode`
- `applicationConnectorType="azuread"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft Entra ID Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Entra ID Request nodes:

- `displayName="Create domain"` `action="CREATE"` `businessObject="Domain"`
- `displayName="Retrieve domains"` `action="RETRIEVEALL"` `businessObject="Domain"`
- `displayName="Retrieve domain"` `action="RETRIEVE"` `businessObject="Domain"`
- `displayName="Update domain"` `action="UPDATEALL"` `businessObject="Domain"`
- `displayName="Upsert domain"` `action="UPSERT"` `businessObject="Domain"`
- `displayName="Delete domain"` `action="DELETEALL"` `businessObject="Domain"`
- `displayName="Create user"` `action="CREATE"` `businessObject="User"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve user"` `action="RETRIEVE"` `businessObject="User"`
- `displayName="Update user"` `action="UPDATEALL"` `businessObject="User"`
- `displayName="Upsert user"` `action="UPSERT"` `businessObject="User"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="User"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Retrieve group"` `action="RETRIEVE"` `businessObject="Group"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="Group"`
- `displayName="Upsert group"` `action="UPSERT"` `businessObject="Group"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="Group"`
- `displayName="Create administrative unit"` `action="CREATE"` `businessObject="AdministrativeUnit"`
- `displayName="Retrieve administrative units"` `action="RETRIEVEALL"` `businessObject="AdministrativeUnit"`
- `displayName="Retrieve administrative unit"` `action="RETRIEVE"` `businessObject="AdministrativeUnit"`
- `displayName="Update administrative unit"` `action="UPDATEALL"` `businessObject="AdministrativeUnit"`
- `displayName="Upsert administrative unit"` `action="UPSERT"` `businessObject="AdministrativeUnit"`
- `displayName="Delete administrative unit"` `action="DELETEALL"` `businessObject="AdministrativeUnit"`
- `displayName="Create device"` `action="CREATE"` `businessObject="Device"`
- `displayName="Retrieve devices"` `action="RETRIEVEALL"` `businessObject="Device"`
- `displayName="Retrieve device"` `action="RETRIEVE"` `businessObject="Device"`
- `displayName="Update device"` `action="UPDATEALL"` `businessObject="Device"`
- `displayName="Upsert device"` `action="UPSERT"` `businessObject="Device"`
- `displayName="Delete device"` `action="DELETEALL"` `businessObject="Device"`
- `displayName="Retrieve organizations"` `action="RETRIEVEALL"` `businessObject="Organization"`
- `displayName="Retrieve organization"` `action="RETRIEVE"` `businessObject="Organization"`
- `displayName="Update organization"` `action="UPDATEALL"` `businessObject="Organization"`
- `displayName="Retrieve group members"` `action="RETRIEVEALL"` `businessObject="GroupMember"`
- `displayName="Retrieve group users"` `action="RETRIEVEALL"` `businessObject="GroupUser"`
- `displayName="Delete group user"` `action="DELETEALL"` `businessObject="GroupUser"`
- `displayName="Retrieve administrative units (groups)"` `action="RETRIEVEALL"` `businessObject="AdministrativeUnitGroup"`
- `displayName="Delete administrative unit (group)"` `action="DELETEALL"` `businessObject="AdministrativeUnitGroup"`
- `displayName="Retrieve administrative units (users)"` `action="RETRIEVEALL"` `businessObject="AdministrativeUnitUser"`
- `displayName="Delete administrative unit (user)"` `action="DELETEALL"` `businessObject="AdministrativeUnitUser"`
- `displayName="Create registered owner"` `action="CREATE"` `businessObject="RegisteredOwner"`
- `displayName="Retrieve registered owners"` `action="RETRIEVEALL"` `businessObject="RegisteredOwner"`
- `displayName="Delete registered owner"` `action="DELETEALL"` `businessObject="RegisteredOwner"`
- `displayName="Create registered user"` `action="CREATE"` `businessObject="RegisteredUser"`
- `displayName="Retrieve registered users"` `action="RETRIEVEALL"` `businessObject="RegisteredUser"`
- `displayName="Delete registered user"` `action="DELETEALL"` `businessObject="RegisteredUser"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AzureAD1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="AzureAD1" policyTemplate="online_v1_basic_oauth" policyType="azuread" shortDescription="" version="">
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
