# Google Calendar

## Purpose
Connector-specific rules for Google Calendar Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Calendar Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Calendar Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlecalendar.msgnode`
- `applicationConnectorType="googlecalendar"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Calendar Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Calendar Request nodes:

- `displayName="Create event"` `action="CREATE"` `businessObject="events"`
- `displayName="Retrieve events"` `action="RETRIEVEALL"` `businessObject="events"`
- `displayName="Update event"` `action="UPDATEALL"` `businessObject="events"`
- `displayName="Delete event"` `action="DELETEALL"` `businessObject="events"`
- `displayName="Copy event"` `action="IMPORTEVENT"` `businessObject="events"`
- `displayName="Move event"` `action="MOVEEVENT"` `businessObject="events"`
- `displayName="Create quick event"` `action="CREATEQUICKEVENT"` `businessObject="events"`
- `displayName="Update or create event"` `action="UPSERTWITHWHERE"` `businessObject="events"`
- `displayName="Create calendar"` `action="CREATE"` `businessObject="calendars"`
- `displayName="Retrieve calendars"` `action="RETRIEVEALL"` `businessObject="calendars"`
- `displayName="Update calendar"` `action="UPDATEALL"` `businessObject="calendars"`
- `displayName="Update calendar"` `action="UPDATE"` `businessObject="calendars"`
- `displayName="Delete calendar"` `action="DELETEALL"` `businessObject="calendars"`
- `displayName="Update or create calendar"` `action="UPSERTWITHWHERE"` `businessObject="calendars"`
- `displayName="Clear calendar"` `action="CLEARCALENDAR"` `businessObject="calendars"`
- `displayName="Check free/busy"` `action="CHECKFREEBUSY"` `businessObject="calendars"`
- `displayName="Retrieve calendar list"` `action="RETRIEVEALL"` `businessObject="calendarlist"`
- `displayName="Update calendar list"` `action="UPDATEALL"` `businessObject="calendarlist"`
- `displayName="Add calendar to calendar list"` `action="ADDCALENDARTOCALENDARLIST"` `businessObject="calendarlist"`
- `displayName="Remove calendar from calendar list"` `action="REMOVECALENDARFROMCALENDARLIST"` `businessObject="calendarlist"`
- `displayName="Create calendar sharing rule"` `action="CREATE"` `businessObject="calendarsharing"`
- `displayName="Retrieve calendar sharing rules"` `action="RETRIEVEALL"` `businessObject="calendarsharing"`
- `displayName="Update calendar sharing rule"` `action="UPDATE"` `businessObject="calendarsharing"`
- `displayName="Update calendar sharing rules"` `action="UPDATEALL"` `businessObject="calendarsharing"`
- `displayName="Delete calendar sharing rule"` `action="DELETEALL"` `businessObject="calendarsharing"`
- `displayName="Update or create calendar sharing rule"` `action="UPSERTWITHWHERE"` `businessObject="calendarsharing"`
- `displayName="Retrieve recurring events"` `action="RETRIEVEALL"` `businessObject="recurringevents"`
- `displayName="Update recurring event"` `action="UPDATEALL"` `businessObject="recurringevents"`
- `displayName="Delete recurring event"` `action="DELETEALL"` `businessObject="recurringevents"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googlecalendar`.
- The policy file is available at `EveryPolicy/googlecalendar.policyxml`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googlecalendar" policyTemplate="online_v1_basic_oauth" policyType="googlecalendar" shortDescription="" version="">
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
- [`loopback-connector-googlecalendar/descriptors/googlecalendar.json`](../loopback-connector-googlecalendar/descriptors/googlecalendar.json)
- [`loopback-connector-googlecalendar/descriptors/googlecalendar.yaml`](../loopback-connector-googlecalendar/descriptors/googlecalendar.yaml)
- [`loopback-connector-googlecalendar/lib/models/objects.json`](../loopback-connector-googlecalendar/lib/models/objects.json)
- [`loopback-connector-googlecalendar/lib/models/events.json`](../loopback-connector-googlecalendar/lib/models/events.json)
- [`loopback-connector-googlecalendar/lib/models/calendars.json`](../loopback-connector-googlecalendar/lib/models/calendars.json)
- [`loopback-connector-googlecalendar/lib/models/calendarlist.json`](../loopback-connector-googlecalendar/lib/models/calendarlist.json)
- [`loopback-connector-googlecalendar/lib/models/calendarsharing.json`](../loopback-connector-googlecalendar/lib/models/calendarsharing.json)
- [`loopback-connector-googlecalendar/lib/models/recurringevents.json`](../loopback-connector-googlecalendar/lib/models/recurringevents.json)
- [`loopback-connector-googlecalendar/lib/util/googleCalendarConstants.json`](../loopback-connector-googlecalendar/lib/util/googleCalendarConstants.json)
- [`EveryPolicy/googlecalendar.policyxml`](../EveryPolicy/googlecalendar.policyxml)
