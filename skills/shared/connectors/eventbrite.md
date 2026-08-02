# Eventbrite

## Purpose
Connector-specific rules for Eventbrite Request nodes.

## When to use
Use this document when the requested ACE flow includes an Eventbrite Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Eventbrite Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_eventbrite.msgnode`
- `applicationConnectorType="eventbrite"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Eventbrite Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Eventbrite Request nodes:

- `displayName="Retrieve organizations"` `action="RETRIEVEALL"` `businessObject="Organization"`
- `displayName="Create event"` `action="CREATE"` `businessObject="Event"`
- `displayName="Retrieve events"` `action="RETRIEVEALL"` `businessObject="Event"`
- `displayName="Retrieve event by ID"` `action="RETRIEVE"` `businessObject="Event"`
- `displayName="Update event"` `action="UPDATE"` `businessObject="Event"`
- `displayName="Delete event"` `action="DELETEALL"` `businessObject="Event"`
- `displayName="Retrieve order by ID"` `action="RETRIEVE"` `businessObject="Order"`
- `displayName="Retrieve attendees"` `action="RETRIEVEALL"` `businessObject="Attendee"`
- `displayName="Retrieve attendee by ID"` `action="RETRIEVE"` `businessObject="Attendee"`
- `displayName="Create organizer"` `action="CREATE"` `businessObject="Organizer"`
- `displayName="Retrieve organizers"` `action="RETRIEVEALL"` `businessObject="Organizer"`
- `displayName="Update organizer"` `action="UPDATE"` `businessObject="Organizer"`
- `displayName="Create contact list"` `action="CREATE"` `businessObject="ContactList"`
- `displayName="Retrieve contact lists"` `action="RETRIEVEALL"` `businessObject="ContactList"`
- `displayName="Update contact list"` `action="UPDATEALL"` `businessObject="ContactList"`
- `displayName="Delete contact list"` `action="DELETEALL"` `businessObject="ContactList"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contact"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contact"`

## Webhook event triggers
The following webhook event triggers are supported via the `webhooks-connector-eventbrite`. These are used in trigger-style flows rather than Request nodes:

- `displayName="Event created"` `event="event.created"` `businessObject="Event"`
- `displayName="Event updated"` `event="event.updated"` `businessObject="Event"`
- `displayName="Event published"` `event="event.published"` `businessObject="Event"`
- `displayName="Event unpublished"` `event="event.unpublished"` `businessObject="Event"`
- `displayName="Order placed"` `event="order.placed"` `businessObject="Order"`
- `displayName="Order updated"` `event="order.updated"` `businessObject="Order"`
- `displayName="Order refunded"` `event="order.refunded"` `businessObject="Order"`
- `displayName="Attendee updated"` `event="attendee.updated"` `businessObject="Attendee"`
- `displayName="Attendee checked in"` `event="attendee.checked_in"` `businessObject="Attendee"`
- `displayName="Attendee checked out"` `event="attendee.checked_out"` `businessObject="Attendee"`
- `displayName="Organizer updated"` `event="organizer.updated"` `businessObject="Organizer"`
- `displayName="Venue updated"` `event="venue.updated"` `businessObject="Venue"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Eventbrite1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Eventbrite1" policyTemplate="online_v1_basic_oauth" policyType="eventbrite" shortDescription="" version="">
        <credentialName>EventbriteCredential</credentialName>
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
