# LDAP

## Purpose
Connector-specific rules for LDAP Request and LDAP Input nodes.

## When to use
Use this document when the requested ACE flow includes an LDAP Request node or LDAP Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- LDAP Request node
- LDAP Input node

## Required node attributes
### LDAP Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ldap.msgnode`
- `applicationConnectorType="ldap"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### LDAP Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_ldap.msgnode`
- `applicationConnectorType="ldap"`

## Schema file requirements
For LDAP Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for LDAP Request nodes:

- `displayName="Create entry"` `action="CREATE"` `businessObject="Entry"`
- `displayName="Retrieve entries"` `action="RETRIEVEALL"` `businessObject="Entry"`
- `displayName="Update entry"` `action="UPDATEALL"` `businessObject="Entry"`
- `displayName="Delete entry"` `action="DELETEALL"` `businessObject="Entry"`
- `displayName="Modify distinguished name"` `action="MODIFYDN"` `businessObject="Entry"`
- `displayName="Create device"` `action="CREATE"` `businessObject="Device"`
- `displayName="Retrieve devices"` `action="RETRIEVEALL"` `businessObject="Device"`
- `displayName="Update device"` `action="UPDATEALL"` `businessObject="Device"`
- `displayName="Delete device"` `action="DELETEALL"` `businessObject="Device"`
- `displayName="Create inetOrgPerson"` `action="CREATE"` `businessObject="InetOrgPerson"`
- `displayName="Retrieve inetOrgPersons"` `action="RETRIEVEALL"` `businessObject="InetOrgPerson"`
- `displayName="Update inetOrgPerson"` `action="UPDATEALL"` `businessObject="InetOrgPerson"`
- `displayName="Delete inetOrgPerson"` `action="DELETEALL"` `businessObject="InetOrgPerson"`
- `displayName="Create organizational person"` `action="CREATE"` `businessObject="OrganizationalPerson"`
- `displayName="Retrieve organizational persons"` `action="RETRIEVEALL"` `businessObject="OrganizationalPerson"`
- `displayName="Update organizational person"` `action="UPDATEALL"` `businessObject="OrganizationalPerson"`
- `displayName="Delete organizational person"` `action="DELETEALL"` `businessObject="OrganizationalPerson"`
- `displayName="Create organizational unit"` `action="CREATE"` `businessObject="OrganizationalUnit"`
- `displayName="Retrieve organizational units"` `action="RETRIEVEALL"` `businessObject="OrganizationalUnit"`
- `displayName="Update organizational unit"` `action="UPDATEALL"` `businessObject="OrganizationalUnit"`
- `displayName="Delete organizational unit"` `action="DELETEALL"` `businessObject="OrganizationalUnit"`
- `displayName="Create person"` `action="CREATE"` `businessObject="Person"`
- `displayName="Retrieve persons"` `action="RETRIEVEALL"` `businessObject="Person"`
- `displayName="Update person"` `action="UPDATEALL"` `businessObject="Person"`
- `displayName="Delete person"` `action="DELETEALL"` `businessObject="Person"`
- `displayName="Create room"` `action="CREATE"` `businessObject="Room"`
- `displayName="Retrieve rooms"` `action="RETRIEVEALL"` `businessObject="Room"`
- `displayName="Update room"` `action="UPDATEALL"` `businessObject="Room"`
- `displayName="Delete room"` `action="DELETEALL"` `businessObject="Room"`

The following combinations are allowed for LDAP Input nodes:

- `displayName="New entry"` `action="CREATED"` `businessObject="Entry"`
- `displayName="Updated entry"` `action="UPDATED"` `businessObject="Entry"`
- `displayName="New device"` `action="CREATED"` `businessObject="Device"`
- `displayName="Updated device"` `action="UPDATED"` `businessObject="Device"`
- `displayName="New inetOrgPerson"` `action="CREATED"` `businessObject="InetOrgPerson"`
- `displayName="Updated inetOrgPerson"` `action="UPDATED"` `businessObject="InetOrgPerson"`
- `displayName="New organizational person"` `action="CREATED"` `businessObject="OrganizationalPerson"`
- `displayName="Updated organizational person"` `action="UPDATED"` `businessObject="OrganizationalPerson"`
- `displayName="New organizational unit"` `action="CREATED"` `businessObject="OrganizationalUnit"`
- `displayName="Updated organizational unit"` `action="UPDATED"` `businessObject="OrganizationalUnit"`
- `displayName="New person"` `action="CREATED"` `businessObject="Person"`
- `displayName="Updated person"` `action="UPDATED"` `businessObject="Person"`
- `displayName="New room"` `action="CREATED"` `businessObject="Room"`
- `displayName="Updated room"` `action="UPDATED"` `businessObject="Room"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:LDAP1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="LDAP1" policyTemplate="online_v1_basic" policyType="ldap" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
