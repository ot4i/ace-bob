# Greenhouse

## Purpose
Connector-specific rules for Greenhouse Request nodes.

## When to use
Use this document when the requested ACE flow includes a Greenhouse Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Greenhouse Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_greenhouse.msgnode`
- `applicationConnectorType="greenhouse"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Greenhouse Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Greenhouse Request nodes:

- `displayName="Add application to candidate"` `action="CREATE"` `businessObject="applications"`
- `displayName="Retrieve applications"` `action="RETRIEVEALL"` `businessObject="applications"`
- `displayName="Convert prospect to candidate"` `action="UPDATEALL"` `businessObject="applications"`
- `displayName="New application"` `action="CREATED_POLLER"` `businessObject="applications"`
- `displayName="Updated application"` `action="UPDATED_POLLER"` `businessObject="applications"`
- `displayName="New or updated application"` `action="CREATEDORUPDATED_POLLER"` `businessObject="applications"`
- `displayName="Create candidate"` `action="CREATE"` `businessObject="candidates"`
- `displayName="Retrieve candidates"` `action="RETRIEVEALL"` `businessObject="candidates"`
- `displayName="Update candidate"` `action="UPDATEALL"` `businessObject="candidates"`
- `displayName="Update or create candidate"` `action="UPSERTWITHWHERE"` `businessObject="candidates"`
- `displayName="Add attachment to candidate"` `action="ADD_ATTACHMENT"` `businessObject="attachment"`
- `displayName="Add attachment to application"` `action="ADD_ATTACHMENT_TO_APPLICATION"` `businessObject="attachment_to_application"`
- `displayName="Create prospect"` `action="CREATE"` `businessObject="prospect"`
- `displayName="Create application for prospect"` `action="CREATE"` `businessObject="application_to_prospect"`
- `displayName="Retrieve job posts"` `action="RETRIEVEALL"` `businessObject="job_posts"`
- `displayName="Create job from existing job"` `action="CREATE"` `businessObject="jobs"`
- `displayName="Retrieve jobs"` `action="RETRIEVEALL"` `businessObject="jobs"`
- `displayName="Update job"` `action="UPDATEALL"` `businessObject="jobs"`
- `displayName="Update or create job"` `action="UPSERTWITHWHERE"` `businessObject="jobs"`
- `displayName="Retrieve job stages"` `action="RETRIEVEALL"` `businessObject="jobStages"`
- `displayName="Create scheduled interview"` `action="CREATE"` `businessObject="scheduled_interview"`
- `displayName="Retrieve scheduled interviews"` `action="RETRIEVEALL"` `businessObject="scheduled_interview"`
- `displayName="Update scheduled interview"` `action="UPDATEALL"` `businessObject="scheduled_interview"`
- `displayName="Delete scheduled interview"` `action="DELETEALL"` `businessObject="scheduled_interview"`
- `displayName="Update or create scheduled interview"` `action="UPSERTWITHWHERE"` `businessObject="scheduled_interview"`
- `displayName="Retrieve scheduled interviews for application"` `action="RETRIEVEALL"` `businessObject="scheduled_interview_application"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="users"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Greenhouse1`.
- This connector uses `applicationType="onprem"` and `authenticationMethod="BASIC_API_KEY"`. The policy includes an `<accountName>` field for the Greenhouse account email ID.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Greenhouse1" policyTemplate="onprem_v1_basic_api_key" policyType="greenhouse" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>onprem</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <accountName/>
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
