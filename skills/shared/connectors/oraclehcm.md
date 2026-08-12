# Oracle HCM

## Purpose
Connector-specific rules for Oracle HCM Request nodes.

## When to use
Use this document when the requested ACE flow includes an Oracle HCM Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Oracle HCM Request node

## Required node attributes
### Oracle HCM Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_oraclehcm.msgnode`
- `applicationConnectorType="oraclehcm"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Oracle HCM Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Oracle HCM Request nodes:

- `displayName="Create job requisition"` `action="CREATE"` `businessObject="jobRequisition"`
- `displayName="Update job requisition"` `action="UPDATEALL"` `businessObject="jobRequisition"`
- `displayName="Delete job requisition"` `action="DELETEALL"` `businessObject="jobRequisition"`
- `displayName="Retrieve job requisitions"` `action="RETRIEVEALL"` `businessObject="jobRequisition"`
- `displayName="Update or create job requisition"` `action="UPSERTWITHWHERE"` `businessObject="jobRequisition"`
- `displayName="Create job requisition attachment"` `action="CREATE"` `businessObject="jobRequisitionAttachment"`
- `displayName="Update job requisition attachment"` `action="UPDATEALL"` `businessObject="jobRequisitionAttachment"`
- `displayName="Delete job requisition attachment"` `action="DELETEALL"` `businessObject="jobRequisitionAttachment"`
- `displayName="Retrieve job requisition attachments"` `action="RETRIEVEALL"` `businessObject="jobRequisitionAttachment"`
- `displayName="Download job requisition attachment content"` `action="DOWNLOADJOBREQFILE"` `businessObject="jobRequisitionAttachment"`
- `displayName="Update or create job requisition attachment"` `action="UPSERTWITHWHERE"` `businessObject="jobRequisitionAttachment"`
- `displayName="Create candidate"` `action="CREATE"` `businessObject="candidate"`
- `displayName="Update candidate"` `action="UPDATEALL"` `businessObject="candidate"`
- `displayName="Delete candidate"` `action="DELETEALL"` `businessObject="candidate"`
- `displayName="Retrieve candidates"` `action="RETRIEVEALL"` `businessObject="candidate"`
- `displayName="Update or create candidate"` `action="UPSERTWITHWHERE"` `businessObject="candidate"`
- `displayName="Create candidate attachment"` `action="CREATE"` `businessObject="candidateAttachment"`
- `displayName="Update candidate attachment"` `action="UPDATEALL"` `businessObject="candidateAttachment"`
- `displayName="Delete candidate attachment"` `action="DELETEALL"` `businessObject="candidateAttachment"`
- `displayName="Retrieve candidate attachments"` `action="RETRIEVEALL"` `businessObject="candidateAttachment"`
- `displayName="Download candidate attachment content"` `action="DOWNLOADCANDIDATEFILE"` `businessObject="candidateAttachment"`
- `displayName="Update or create candidate attachment"` `action="UPSERTWITHWHERE"` `businessObject="candidateAttachment"`
- `displayName="Create candidate education"` `action="CREATE"` `businessObject="candidateEducation"`
- `displayName="Update candidate education"` `action="UPDATEALL"` `businessObject="candidateEducation"`
- `displayName="Delete candidate education"` `action="DELETEALL"` `businessObject="candidateEducation"`
- `displayName="Retrieve candidate education"` `action="RETRIEVEALL"` `businessObject="candidateEducation"`
- `displayName="Update or create candidate education"` `action="UPSERTWITHWHERE"` `businessObject="candidateEducation"`
- `displayName="Create candidate experience"` `action="CREATE"` `businessObject="candidateExperience"`
- `displayName="Update candidate experience"` `action="UPDATEALL"` `businessObject="candidateExperience"`
- `displayName="Delete candidate experience"` `action="DELETEALL"` `businessObject="candidateExperience"`
- `displayName="Retrieve candidate experiences"` `action="RETRIEVEALL"` `businessObject="candidateExperience"`
- `displayName="Update or create candidate experience"` `action="UPSERTWITHWHERE"` `businessObject="candidateExperience"`
- `displayName="Create candidate licence and certification"` `action="CREATE"` `businessObject="candidateLicenceCertification"`
- `displayName="Update candidate licence and certification"` `action="UPDATEALL"` `businessObject="candidateLicenceCertification"`
- `displayName="Delete candidate licence and certification"` `action="DELETEALL"` `businessObject="candidateLicenceCertification"`
- `displayName="Retrieve candidate licences and certifications"` `action="RETRIEVEALL"` `businessObject="candidateLicenceCertification"`
- `displayName="Update or create candidate license and certification"` `action="UPSERTWITHWHERE"` `businessObject="candidateLicenceCertification"`
- `displayName="Retrieve campaign details"` `action="RETRIEVEALL"` `businessObject="campaignDetail"`
- `displayName="Create worker"` `action="CREATE"` `businessObject="worker"`
- `displayName="Update worker"` `action="UPDATEALL"` `businessObject="worker"`
- `displayName="Retrieve workers"` `action="RETRIEVEALL"` `businessObject="worker"`
- `displayName="Update or create worker"` `action="UPSERTWITHWHERE"` `businessObject="worker"`
- `displayName="Create worker assignment"` `action="CREATE"` `businessObject="workerAssignment"`
- `displayName="Update worker assignment"` `action="UPDATEALL"` `businessObject="workerAssignment"`
- `displayName="Delete worker assignment"` `action="DELETEALL"` `businessObject="workerAssignment"`
- `displayName="Retrieve worker assignments"` `action="RETRIEVEALL"` `businessObject="workerAssignment"`
- `displayName="Update or create worker assignment"` `action="UPSERTWITHWHERE"` `businessObject="workerAssignment"`
- `displayName="Retrieve direct reports"` `action="RETRIEVEALL"` `businessObject="directReport"`
- `displayName="Retrieve worker reports"` `action="RETRIEVEALL"` `businessObject="workerReport"`
- `displayName="Create talent person profile"` `action="CREATE"` `businessObject="talentPersonProfile"`
- `displayName="Update talent person profile"` `action="UPDATEALL"` `businessObject="talentPersonProfile"`
- `displayName="Retrieve talent person profiles"` `action="RETRIEVEALL"` `businessObject="talentPersonProfile"`
- `displayName="Update or create talent person profile"` `action="UPSERTWITHWHERE"` `businessObject="talentPersonProfile"`
- `displayName="Create talent person profile attachment"` `action="CREATE"` `businessObject="talentPersonProfileAttachment"`
- `displayName="Delete talent person profile attachment"` `action="DELETEALL"` `businessObject="talentPersonProfileAttachment"`
- `displayName="Retrieve talent person profile attachments"` `action="RETRIEVEALL"` `businessObject="talentPersonProfileAttachment"`
- `displayName="Download talent person profile attachment content"` `action="DOWNLOADTALENTPROFILEFILE"` `businessObject="talentPersonProfileAttachment"`
- `displayName="Create talent person profile work history"` `action="CREATE"` `businessObject="talentPersonProfileWorkHistory"`
- `displayName="Update talent person profile work history"` `action="UPDATEALL"` `businessObject="talentPersonProfileWorkHistory"`
- `displayName="Delete talent person profile work history"` `action="DELETEALL"` `businessObject="talentPersonProfileWorkHistory"`
- `displayName="Retrieve talent person profile work histories"` `action="RETRIEVEALL"` `businessObject="talentPersonProfileWorkHistory"`
- `displayName="Update or create talent person profile work history"` `action="UPSERTWITHWHERE"` `businessObject="talentPersonProfileWorkHistory"`
- `displayName="Create talent competency"` `action="CREATE"` `businessObject="talentCompetency"`
- `displayName="Update talent competency"` `action="UPDATEALL"` `businessObject="talentCompetency"`
- `displayName="Delete talent competency"` `action="DELETEALL"` `businessObject="talentCompetency"`
- `displayName="Retrieve talent competencies"` `action="RETRIEVEALL"` `businessObject="talentCompetency"`
- `displayName="Update or create talent competency"` `action="UPSERTWITHWHERE"` `businessObject="talentCompetency"`
- `displayName="Create talent certification"` `action="CREATE"` `businessObject="talentCertification"`
- `displayName="Update talent certification"` `action="UPDATEALL"` `businessObject="talentCertification"`
- `displayName="Delete talent certification"` `action="DELETEALL"` `businessObject="talentCertification"`
- `displayName="Retrieve talent certifications"` `action="RETRIEVEALL"` `businessObject="talentCertification"`
- `displayName="Update or create talent certification"` `action="UPSERTWITHWHERE"` `businessObject="talentCertification"`
- `displayName="Retrieve performance evaluations"` `action="RETRIEVEALL"` `businessObject="performanceEvaluation"`
- `displayName="Retrieve performance goals"` `action="RETRIEVEALL"` `businessObject="performanceGoal"`
- `displayName="Create absence record"` `action="CREATE"` `businessObject="absenceRecord"`
- `displayName="Update absence record"` `action="UPDATEALL"` `businessObject="absenceRecord"`
- `displayName="Retrieve absence records"` `action="RETRIEVEALL"` `businessObject="absenceRecord"`
- `displayName="Update or create absence record"` `action="UPSERTWITHWHERE"` `businessObject="absenceRecord"`
- `displayName="Retrieve absence plan balances"` `action="RETRIEVEALL"` `businessObject="absencePlanBalance"`
- `displayName="Create salary"` `action="CREATE"` `businessObject="salary"`
- `displayName="Update salary"` `action="UPDATEALL"` `businessObject="salary"`
- `displayName="Delete salary"` `action="DELETEALL"` `businessObject="salary"`
- `displayName="Retrieve salaries"` `action="RETRIEVEALL"` `businessObject="salary"`
- `displayName="Update or create salary"` `action="UPSERTWITHWHERE"` `businessObject="salary"`
- `displayName="Create salary component"` `action="CREATE"` `businessObject="salaryComponent"`
- `displayName="Update salary component"` `action="UPDATEALL"` `businessObject="salaryComponent"`
- `displayName="Delete salary component"` `action="DELETEALL"` `businessObject="salaryComponent"`
- `displayName="Retrieve salary components"` `action="RETRIEVEALL"` `businessObject="salaryComponent"`
- `displayName="Update or create salary component"` `action="UPSERTWITHWHERE"` `businessObject="salaryComponent"`
- `displayName="Create personal payment method"` `action="CREATE"` `businessObject="personalPaymentMethod"`
- `displayName="Update personal payment method"` `action="UPDATEALL"` `businessObject="personalPaymentMethod"`
- `displayName="Delete personal payment method"` `action="DELETEALL"` `businessObject="personalPaymentMethod"`
- `displayName="Retrieve personal payment methods"` `action="RETRIEVEALL"` `businessObject="personalPaymentMethod"`
- `displayName="Update or create personal payment method"` `action="UPSERTWITHWHERE"` `businessObject="personalPaymentMethod"`
- `displayName="Retrieve payslips"` `action="RETRIEVEALL"` `businessObject="payslip"`
- `displayName="Create assigned payroll"` `action="CREATEASSIGNEDPAYROLL"` `businessObject="payroll"`
- `displayName="Create time record event request"` `action="CREATE"` `businessObject="timeRecordEventRequest"`
- `displayName="Update time record event request"` `action="UPDATEALL"` `businessObject="timeRecordEventRequest"`
- `displayName="Retrieve time record event requests"` `action="RETRIEVEALL"` `businessObject="timeRecordEventRequest"`
- `displayName="Delete time record event request"` `action="DELETETIMERECORD"` `businessObject="timeRecordEventRequest"`
- `displayName="Update or create time record event request"` `action="UPSERTWITHWHERE"` `businessObject="timeRecordEventRequest"`
- `displayName="Retrieve time records"` `action="RETRIEVEALL"` `businessObject="timeRecord"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Oraclehcm1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Oraclehcm1" policyTemplate="online_v1_basic" policyType="oraclehcm" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
