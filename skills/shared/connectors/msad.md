# Microsoft Active Directory

## Purpose
Connector-specific rules for Microsoft Active Directory Request and Microsoft Active Directory Input nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Active Directory Request node or Microsoft Active Directory Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Active Directory Request node
- Microsoft Active Directory Input node

## Required node attributes
### Microsoft Active Directory Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msad.msgnode`
- `applicationConnectorType="msad"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Microsoft Active Directory Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_msad.msgnode`
- `applicationConnectorType="msad"`

## Schema file requirements
For Microsoft Active Directory Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Active Directory Request nodes:

- `displayName="Create entry"` `action="CREATE"` `businessObject="Entry"`
- `displayName="Retrieve entries"` `action="RETRIEVEALL"` `businessObject="Entry"`
- `displayName="Update entry"` `action="UPDATEALL"` `businessObject="Entry"`
- `displayName="Delete entry"` `action="DELETEALL"` `businessObject="Entry"`
- `displayName="Check if entry exists"` `action="EXISTS"` `businessObject="Entry"`
- `displayName="Modify distinguished name"` `action="MODIFYDN"` `businessObject="Entry"`
- `displayName="Add entries to group"` `action="ADDTOGROUP"` `businessObject="Entry"`
- `displayName="Remove entries from group"` `action="REMOVEFROMGROUP"` `businessObject="Entry"`
- `displayName="Create computer"` `action="CREATE"` `businessObject="Computer"`
- `displayName="Retrieve computers"` `action="RETRIEVEALL"` `businessObject="Computer"`
- `displayName="Update computer"` `action="UPDATEALL"` `businessObject="Computer"`
- `displayName="Delete computer"` `action="DELETEALL"` `businessObject="Computer"`
- `displayName="Create user"` `action="CREATE"` `businessObject="User"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Update user"` `action="UPDATEALL"` `businessObject="User"`
- `displayName="Delete user"` `action="DELETEALL"` `businessObject="User"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="Group"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="Group"`
- `displayName="Create inetOrgPerson"` `action="CREATE"` `businessObject="InetOrgPerson"`
- `displayName="Retrieve inetOrgPersons"` `action="RETRIEVEALL"` `businessObject="InetOrgPerson"`
- `displayName="Update inetOrgPerson"` `action="UPDATEALL"` `businessObject="InetOrgPerson"`
- `displayName="Delete inetOrgPerson"` `action="DELETEALL"` `businessObject="InetOrgPerson"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contact"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contact"`
- `displayName="Create organizational unit"` `action="CREATE"` `businessObject="OrganizationalUnit"`
- `displayName="Retrieve organizational units"` `action="RETRIEVEALL"` `businessObject="OrganizationalUnit"`
- `displayName="Update organizational unit"` `action="UPDATEALL"` `businessObject="OrganizationalUnit"`
- `displayName="Delete organizational unit"` `action="DELETEALL"` `businessObject="OrganizationalUnit"`

The following combinations are allowed for Microsoft Active Directory Input nodes:

- `displayName="New entry"` `action="CREATED"` `businessObject="Entry"`
- `displayName="Updated entry"` `action="UPDATED"` `businessObject="Entry"`
- `displayName="New computer"` `action="CREATED"` `businessObject="Computer"`
- `displayName="Updated computer"` `action="UPDATED"` `businessObject="Computer"`
- `displayName="New user"` `action="CREATED"` `businessObject="User"`
- `displayName="Updated user"` `action="UPDATED"` `businessObject="User"`
- `displayName="New group"` `action="CREATED"` `businessObject="Group"`
- `displayName="Updated group"` `action="UPDATED"` `businessObject="Group"`
- `displayName="New inetOrgPerson"` `action="CREATED"` `businessObject="InetOrgPerson"`
- `displayName="Updated inetOrgPerson"` `action="UPDATED"` `businessObject="InetOrgPerson"`
- `displayName="New contact"` `action="CREATED"` `businessObject="Contact"`
- `displayName="Updated contact"` `action="UPDATED"` `businessObject="Contact"`
- `displayName="New organizational unit"` `action="CREATED"` `businessObject="OrganizationalUnit"`
- `displayName="Updated organizational unit"` `action="UPDATED"` `businessObject="OrganizationalUnit"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSAD1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSAD1" policyTemplate="online_v1_basic" policyType="msad" shortDescription="" version="">
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
