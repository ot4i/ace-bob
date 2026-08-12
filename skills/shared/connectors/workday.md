# Workday

## Purpose
Connector-specific rules for Workday Request nodes.

## When to use
Use this document when the requested ACE flow includes a Workday Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Workday Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_workday.msgnode`
- `applicationConnectorType="workday"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Workday Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Workday Request nodes:

- `displayName="Get Candidates"` `action="Get_Candidates"` `businessObject="Recruiting___Get_Candidates"`
- `displayName="Find Organization"` `action="Find_Organization"` `businessObject="Human_Resources___Find_Organization"`
- `displayName="Get Period Schedules"` `action="Get_Period_Schedules"` `businessObject="Payroll_Interface___Get_Period_Schedules"`
- `displayName="Get Worker Costing Allocations"` `action="Get_Worker_Costing_Allocations"` `businessObject="Payroll_Interface___Get_Worker_Costing_Allocations"`
- `displayName="Get Time Off Plan Balances"` `action="Get_Time_Off_Plan_Balances"` `businessObject="Absence_Management___Get_Time_Off_Plan_Balances"`
- `displayName="Get Payments"` `action="Get_Payments"` `businessObject="Cash_Management___Get_Payments"`
- `displayName="Get Bank Statements"` `action="Get_Bank_Statements"` `businessObject="Cash_Management___Get_Bank_Statements"`
- `displayName="Get Statistics"` `action="Get_Statistics"` `businessObject="Financial_Management___Get_Statistics"`
- `displayName="Get Business Plan Details"` `action="Get_Business_Plan_Details"` `businessObject="Financial_Management___Get_Business_Plan_Details"`
- `displayName="Get Timesheets"` `action="Get_Timesheets"` `businessObject="Resource_Management___Get_Timesheets"`
- `displayName="Get Projects"` `action="Get_Projects"` `businessObject="Resource_Management___Get_Projects"`
- `displayName="Get Degrees"` `action="Get_Degrees"` `businessObject="Performance_Management___Get_Degrees"`
- `displayName="Put Degree"` `action="Put_Degree"` `businessObject="Performance_Management___Put_Degree"`
- `displayName="Put Time Clock Events"` `action="Put_Time_Clock_Events"` `businessObject="Time_Tracking___Put_Time_Clock_Events"`
- `displayName="Import Time Clock Events"` `action="Import_Time_Clock_Events"` `businessObject="Time_Tracking___Import_Time_Clock_Events"`
- `displayName="Get Job History Companies"` `action="Get_Job_History_Companies"` `businessObject="Talent___Get_Job_History_Companies"`
- `displayName="Put Job History Company"` `action="Put_Job_History_Company"` `businessObject="Talent___Put_Job_History_Company"`
- `displayName="Get Change Licenses"` `action="Get_Change_Licenses"` `businessObject="Student_Records___Get_Change_Licenses"`
- `displayName="Get Subscriptions"` `action="Get_Subscriptions"` `businessObject="Integrations___Get_Subscriptions"`
- `displayName="Get Learning Enrollments"` `action="Get_Learning_Enrollments"` `businessObject="Learning___Get_Learning_Enrollments"`
- `displayName="Put Sequence Generator"` `action="Put_Sequence_Generator"` `businessObject="Integrations___Put_Sequence_Generator"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Workday1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Workday1" policyTemplate="online_v1_basic" policyType="workday" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <domainName/>
        <tenantId/>
        <apiVersion>v41.2</apiVersion>
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
