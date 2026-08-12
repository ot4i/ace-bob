# SAP SuccessFactors

## Purpose
Connector-specific rules for SAP SuccessFactors Request nodes.

## When to use
Use this document when the requested ACE flow includes a SAP SuccessFactors Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- SAP SuccessFactors Request node

## Required node attributes
### SAP SuccessFactors Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_sapsuccessfactors.msgnode`
- `applicationConnectorType="sapsuccessfactors"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For SAP SuccessFactors Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for SAP SuccessFactors Request nodes:

- `displayName="Create candidate"` `action="CREATE"` `businessObject="Candidate"`
- `displayName="Retrieve candidates"` `action="RETRIEVEALL"` `businessObject="Candidate"`
- `displayName="Retrieve candidate"` `action="RETRIEVE"` `businessObject="Candidate"`
- `displayName="Update candidate"` `action="UPDATEALL"` `businessObject="Candidate"`
- `displayName="Create job application interview"` `action="CREATE"` `businessObject="JobApplicationInterview"`
- `displayName="Retrieve job application interviews"` `action="RETRIEVEALL"` `businessObject="JobApplicationInterview"`
- `displayName="Retrieve job application interview"` `action="RETRIEVE"` `businessObject="JobApplicationInterview"`
- `displayName="Update job application interview"` `action="UPDATEALL"` `businessObject="JobApplicationInterview"`
- `displayName="Delete job application interview"` `action="DELETEALL"` `businessObject="JobApplicationInterview"`
- `displayName="Retrieve job applications"` `action="RETRIEVEALL"` `businessObject="JobApplication"`
- `displayName="Retrieve job application"` `action="RETRIEVE"` `businessObject="JobApplication"`
- `displayName="Update job application"` `action="UPDATEALL"` `businessObject="JobApplication"`
- `displayName="Retrieve job application statuses"` `action="RETRIEVEALL"` `businessObject="JobApplicationStatus"`
- `displayName="Create job requisition"` `action="CREATE"` `businessObject="JobRequisition"`
- `displayName="Retrieve job requisitions"` `action="RETRIEVEALL"` `businessObject="JobRequisition"`
- `displayName="Retrieve job requisition"` `action="RETRIEVE"` `businessObject="JobRequisition"`
- `displayName="Update job requisition"` `action="UPDATEALL"` `businessObject="JobRequisition"`
- `displayName="Delete job requisition"` `action="DELETEALL"` `businessObject="JobRequisition"`
- `displayName="Retrieve onboarding candidate information"` `action="RETRIEVEALL"` `businessObject="OnboardingCandidateInfo"`
- `displayName="Retrieve onboarding candidate information by ID"` `action="RETRIEVE"` `businessObject="OnboardingCandidateInfo"`
- `displayName="Update onboarding candidate information"` `action="UPDATEALL"` `businessObject="OnboardingCandidateInfo"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:SapSuccessFactors1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="SapSuccessFactors1" policyTemplate="online_v1_basic" policyType="sapsuccessfactors" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <domainName>https://apisalesdemo2.successfactors.eu/odata/v2</domainName>
        <isTlsEnabled>false</isTlsEnabled>
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
