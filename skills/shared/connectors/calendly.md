# Calendly

## Purpose
Connector-specific rules for Calendly Request nodes.

## When to use
Use this document when the requested ACE flow includes a Calendly Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Calendly Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_calendly.msgnode`
- `applicationConnectorType="calendly"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Calendly Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Calendly Request nodes:

- `displayName="Retrieve event types"` `action="RETRIEVEALL"` `businessObject="eventType"`
- `displayName="Retrieve account details"` `action="GETCURRENTUSER"` `businessObject="user"`
- `displayName="Create single use scheduling link"` `action="CREATE"` `businessObject="schedulingLink"`
- `displayName="Retrieve scheduled events"` `action="RETRIEVEALL"` `businessObject="event"`
- `displayName="Cancel event"` `action="CANCELEVENT"` `businessObject="event"`
- `displayName="Retrieve event invitees"` `action="RETRIEVEALL"` `businessObject="eventInvitee"`
- `displayName="Mark event invitee as no show"` `action="MARKINVITEENOSHOW"` `businessObject="eventInvitee"`
- `displayName="Undo mark event invitee as no show"` `action="UNDOMARKINVITEENOSHOW"` `businessObject="eventInvitee"`
- `displayName="Retrieve organization memberships"` `action="RETRIEVEALL"` `businessObject="organizationMembership"`
- `displayName="Delete organization membership"` `action="DELETEALL"` `businessObject="organizationMembership"`
- `displayName="Create organization invitation"` `action="CREATE"` `businessObject="organizationInvitation"`
- `displayName="Retrieve organization invitations"` `action="RETRIEVEALL"` `businessObject="organizationInvitation"`
- `displayName="Delete organization invitation"` `action="DELETEALL"` `businessObject="organizationInvitation"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Calendly1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Calendly1" policyTemplate="online_v1_basic" policyType="calendly" shortDescription="" version="">
        <credentialName>CalendlyCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
