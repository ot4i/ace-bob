# Freshservice

## Purpose
Connector-specific rules for Freshservice Request nodes.

## When to use
Use this document when the requested ACE flow includes a Freshservice Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Freshservice Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_freshservice.msgnode`
- `applicationConnectorType="freshservice"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Freshservice Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Freshservice Request nodes:

- `displayName="Create ticket"` `action="CREATE"` `businessObject="Tickets"`
- `displayName="Retrieve tickets"` `action="RETRIEVEWITHWHERE"` `businessObject="Tickets"`
- `displayName="Retrieve ticket by ID"` `action="RETRIEVE"` `businessObject="Tickets"`
- `displayName="View tickets"` `action="CUSTOM"` `businessObject="Tickets"`
- `displayName="Update ticket"` `action="UPDATE"` `businessObject="Tickets"`
- `displayName="Delete ticket"` `action="DELETE"` `businessObject="Tickets"`
- `displayName="Create requester"` `action="CREATE"` `businessObject="Requesters"`
- `displayName="Retrieve requesters"` `action="RETRIEVEWITHWHERE"` `businessObject="Requesters"`
- `displayName="Retrieve requester by ID"` `action="RETRIEVE"` `businessObject="Requesters"`
- `displayName="Filter requesters"` `action="CUSTOM"` `businessObject="Requesters"`
- `displayName="Update requester"` `action="UPDATE"` `businessObject="Requesters"`
- `displayName="Delete requester"` `action="DELETE"` `businessObject="Requesters"`
- `displayName="Create requester group"` `action="CREATE"` `businessObject="Requester groups"`
- `displayName="Retrieve all requester groups"` `action="RETRIEVEWITHWHERE"` `businessObject="Requester groups"`
- `displayName="Retrieve requester group by ID"` `action="RETRIEVE"` `businessObject="Requester groups"`
- `displayName="Update requester group"` `action="UPDATE"` `businessObject="Requester groups"`
- `displayName="Delete requester group"` `action="DELETE"` `businessObject="Requester groups"`
- `displayName="Create agent group"` `action="CREATE"` `businessObject="Agent groups"`
- `displayName="Retrieve all agent groups"` `action="RETRIEVEWITHWHERE"` `businessObject="Agent groups"`
- `displayName="Retrieve agent group by ID"` `action="RETRIEVE"` `businessObject="Agent groups"`
- `displayName="Update agent group"` `action="UPDATE"` `businessObject="Agent groups"`
- `displayName="Delete agent group"` `action="DELETE"` `businessObject="Agent groups"`
- `displayName="Create agent"` `action="CREATE"` `businessObject="Agents"`
- `displayName="Retrieve agents"` `action="RETRIEVEWITHWHERE"` `businessObject="Agents"`
- `displayName="Retrieve agent by ID"` `action="RETRIEVE"` `businessObject="Agents"`
- `displayName="Filter agents"` `action="CUSTOM"` `businessObject="Agents"`
- `displayName="Update agent"` `action="UPDATE"` `businessObject="Agents"`
- `displayName="Delete agent"` `action="DELETE"` `businessObject="Agents"`
- `displayName="Create department"` `action="CREATE"` `businessObject="Departments"`
- `displayName="Retrieve all departments"` `action="RETRIEVEWITHWHERE"` `businessObject="Departments"`
- `displayName="Retrieve department by ID"` `action="RETRIEVE"` `businessObject="Departments"`
- `displayName="Update department"` `action="UPDATE"` `businessObject="Departments"`
- `displayName="Delete department"` `action="DELETE"` `businessObject="Departments"`
- `displayName="Create note"` `action="CUSTOM"` `businessObject="Conversations"`
- `displayName="Create reply"` `action="CUSTOM"` `businessObject="Conversations"`
- `displayName="Retrieve conversations"` `action="RETRIEVEWITHWHERE"` `businessObject="Conversations"`
- `displayName="Update conversation"` `action="UPDATE"` `businessObject="Conversations"`
- `displayName="Delete conversation"` `action="DELETE"` `businessObject="Conversations"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Tasks"`
- `displayName="Retrieve tasks"` `action="RETRIEVEWITHWHERE"` `businessObject="Tasks"`
- `displayName="Retrieve task by ID"` `action="RETRIEVE"` `businessObject="Tasks"`
- `displayName="Update task"` `action="UPDATE"` `businessObject="Tasks"`
- `displayName="Delete task"` `action="DELETE"` `businessObject="Tasks"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Freshservice1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Freshservice1" policyTemplate="online_v1_basic_api_key" policyType="freshservice" shortDescription="" version="">
        <credentialName>FreshserviceCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <apiUrl/>
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
