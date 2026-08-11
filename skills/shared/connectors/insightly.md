# Insightly

## Purpose
Connector-specific rules for Insightly Request and Insightly Input nodes.

## When to use
Use this document when the requested ACE flow includes an Insightly Request node or Insightly Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Insightly Request node
- Insightly Input node

## Required node attributes
### Insightly Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_insightly.msgnode`
- `applicationConnectorType="insightly"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Insightly Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_insightly.msgnode`
- `applicationConnectorType="insightly"`

## Schema file requirements
For Insightly Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Insightly Request nodes:

- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contact"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contact"`
- `displayName="Retrieve contact emails"` `action="RETRIEVEALL"` `businessObject="ContactEmail"`
- `displayName="Retrieve contact notes"` `action="RETRIEVEALL"` `businessObject="ContactNote"`
- `displayName="Retrieve contact tasks"` `action="RETRIEVEALL"` `businessObject="ContactTask"`
- `displayName="Retrieve email"` `action="RETRIEVEALL"` `businessObject="Email"`
- `displayName="Delete email"` `action="DELETEALL"` `businessObject="Email"`
- `displayName="Create event"` `action="CREATE"` `businessObject="Event"`
- `displayName="Retrieve events"` `action="RETRIEVEALL"` `businessObject="Event"`
- `displayName="Update event"` `action="UPDATEALL"` `businessObject="Event"`
- `displayName="Delete event"` `action="DELETEALL"` `businessObject="Event"`
- `displayName="Create lead"` `action="CREATE"` `businessObject="Lead"`
- `displayName="Retrieve leads"` `action="RETRIEVEALL"` `businessObject="Lead"`
- `displayName="Update lead"` `action="UPDATEALL"` `businessObject="Lead"`
- `displayName="Delete lead"` `action="DELETEALL"` `businessObject="Lead"`
- `displayName="Retrieve lead emails"` `action="RETRIEVEALL"` `businessObject="LeadEmail"`
- `displayName="Retrieve lead notes"` `action="RETRIEVEALL"` `businessObject="LeadNote"`
- `displayName="Retrieve lead tasks"` `action="RETRIEVEALL"` `businessObject="LeadTask"`
- `displayName="Create lead source"` `action="CREATE"` `businessObject="LeadSource"`
- `displayName="Retrieve lead sources"` `action="RETRIEVEALL"` `businessObject="LeadSource"`
- `displayName="Update lead source"` `action="UPDATEALL"` `businessObject="LeadSource"`
- `displayName="Delete lead source"` `action="DELETEALL"` `businessObject="LeadSource"`
- `displayName="Create lead status"` `action="CREATE"` `businessObject="LeadStatus"`
- `displayName="Retrieve lead statuses"` `action="RETRIEVEALL"` `businessObject="LeadStatus"`
- `displayName="Update lead status"` `action="UPDATEALL"` `businessObject="LeadStatus"`
- `displayName="Delete lead status"` `action="DELETEALL"` `businessObject="LeadStatus"`
- `displayName="Create opportunity"` `action="CREATE"` `businessObject="Opportunity"`
- `displayName="Retrieve opportunities"` `action="RETRIEVEALL"` `businessObject="Opportunity"`
- `displayName="Update opportunity"` `action="UPDATEALL"` `businessObject="Opportunity"`
- `displayName="Delete opportunity"` `action="DELETEALL"` `businessObject="Opportunity"`
- `displayName="Retrieve opportunity emails"` `action="RETRIEVEALL"` `businessObject="OpportunityEmail"`
- `displayName="Retrieve opportunity notes"` `action="RETRIEVEALL"` `businessObject="OpportunityNote"`
- `displayName="Retrieve opportunity tasks"` `action="RETRIEVEALL"` `businessObject="OpportunityTask"`
- `displayName="Retrieve opportunity state reasons"` `action="RETRIEVEALL"` `businessObject="OpportunityStateReason"`
- `displayName="Create opportunity category"` `action="CREATE"` `businessObject="OpportunityCategory"`
- `displayName="Retrieve opportunity categories"` `action="RETRIEVEALL"` `businessObject="OpportunityCategory"`
- `displayName="Update opportunity category"` `action="UPDATEALL"` `businessObject="OpportunityCategory"`
- `displayName="Delete opportunity category"` `action="DELETEALL"` `businessObject="OpportunityCategory"`
- `displayName="Create organisation"` `action="CREATE"` `businessObject="Organisation"`
- `displayName="Retrieve organisations"` `action="RETRIEVEALL"` `businessObject="Organisation"`
- `displayName="Update organisation"` `action="UPDATEALL"` `businessObject="Organisation"`
- `displayName="Delete organisation"` `action="DELETEALL"` `businessObject="Organisation"`
- `displayName="Retrieve organisation emails"` `action="RETRIEVEALL"` `businessObject="OrganisationEmail"`
- `displayName="Retrieve organisation notes"` `action="RETRIEVEALL"` `businessObject="OrganisationNote"`
- `displayName="Retrieve organisation tasks"` `action="RETRIEVEALL"` `businessObject="OrganisationTask"`
- `displayName="Create project"` `action="CREATE"` `businessObject="Project"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Project"`
- `displayName="Update project"` `action="UPDATEALL"` `businessObject="Project"`
- `displayName="Delete project"` `action="DELETEALL"` `businessObject="Project"`
- `displayName="Retrieve project emails"` `action="RETRIEVEALL"` `businessObject="ProjectEmail"`
- `displayName="Retrieve project notes"` `action="RETRIEVEALL"` `businessObject="ProjectNote"`
- `displayName="Retrieve project tasks"` `action="RETRIEVEALL"` `businessObject="ProjectTask"`
- `displayName="Create project category"` `action="CREATE"` `businessObject="ProjectCategory"`
- `displayName="Retrieve project categories"` `action="RETRIEVEALL"` `businessObject="ProjectCategory"`
- `displayName="Update project category"` `action="UPDATEALL"` `businessObject="ProjectCategory"`
- `displayName="Delete project category"` `action="DELETEALL"` `businessObject="ProjectCategory"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Task"`
- `displayName="Retrieve tasks"` `action="RETRIEVEALL"` `businessObject="Task"`
- `displayName="Update task"` `action="UPDATEALL"` `businessObject="Task"`
- `displayName="Delete task"` `action="DELETEALL"` `businessObject="Task"`
- `displayName="Create task category"` `action="CREATE"` `businessObject="TaskCategory"`
- `displayName="Retrieve task categories"` `action="RETRIEVEALL"` `businessObject="TaskCategory"`
- `displayName="Update task category"` `action="UPDATEALL"` `businessObject="TaskCategory"`
- `displayName="Delete task category"` `action="DELETEALL"` `businessObject="TaskCategory"`
- `displayName="Create team"` `action="CREATE"` `businessObject="Team"`
- `displayName="Retrieve teams"` `action="RETRIEVEALL"` `businessObject="Team"`
- `displayName="Update team"` `action="UPDATEALL"` `businessObject="Team"`
- `displayName="Delete team"` `action="DELETEALL"` `businessObject="Team"`
- `displayName="Create team member"` `action="CREATE"` `businessObject="TeamMember"`
- `displayName="Retrieve team members"` `action="RETRIEVEALL"` `businessObject="TeamMember"`
- `displayName="Delete team member"` `action="DELETEALL"` `businessObject="TeamMember"`
- `displayName="Update note"` `action="UPDATEALL"` `businessObject="Note"`
- `displayName="Retrieve notes"` `action="RETRIEVEALL"` `businessObject="Note"`
- `displayName="Delete note"` `action="DELETEALL"` `businessObject="Note"`
- `displayName="Retrieve pipelines"` `action="RETRIEVEALL"` `businessObject="Pipeline"`
- `displayName="Retrieve pipeline stages"` `action="RETRIEVEALL"` `businessObject="PipelineStage"`
- `displayName="Retrieve relationships"` `action="RETRIEVEALL"` `businessObject="Relationship"`
- `displayName="Retrieve custom fields"` `action="RETRIEVEALL"` `businessObject="CustomField"`
- `displayName="Retrieve file categories"` `action="RETRIEVEALL"` `businessObject="FileCategory"`
- `displayName="Retrieve file attachments"` `action="RETRIEVEALL"` `businessObject="FileAttachment"`
- `displayName="Delete file attachment"` `action="DELETEALL"` `businessObject="FileAttachment"`
- `displayName="Retrieve milestones"` `action="RETRIEVEALL"` `businessObject="Milestone"`
- `displayName="Retrieve follows"` `action="RETRIEVEALL"` `businessObject="Follow"`
- `displayName="Retrieve activity sets"` `action="RETRIEVEALL"` `businessObject="ActivitySet"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve countries"` `action="RETRIEVEALL"` `businessObject="Country"`
- `displayName="Retrieve currencies"` `action="RETRIEVEALL"` `businessObject="Currency"`

The following combinations are allowed for Insightly Input nodes:

- `displayName="New contact"` `action="CREATED"` `businessObject="Contact"`
- `displayName="Updated contact"` `action="UPDATED"` `businessObject="Contact"`
- `displayName="New lead"` `action="CREATED"` `businessObject="Lead"`
- `displayName="Updated lead"` `action="UPDATED"` `businessObject="Lead"`
- `displayName="New event"` `action="CREATED"` `businessObject="Event"`
- `displayName="Updated event"` `action="UPDATED"` `businessObject="Event"`
- `displayName="New task"` `action="CREATED"` `businessObject="Task"`
- `displayName="Updated task"` `action="UPDATED"` `businessObject="Task"`
- `displayName="New opportunity"` `action="CREATED"` `businessObject="Opportunity"`
- `displayName="Updated opportunity"` `action="UPDATED"` `businessObject="Opportunity"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Insightly1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Insightly1" policyTemplate="online_v1_basic" policyType="insightly" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiVersion>v3.1</apiVersion>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
