# Microsoft Power BI

## Purpose
Connector-specific rules for Microsoft Power BI Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Power BI Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Power BI Request node

## Required node attributes
### Microsoft Power BI Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_mspowerbi.msgnode`
- `applicationConnectorType="mspowerbi"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft Power BI Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Power BI Request nodes:

- `displayName="Create workspace"` `action="CREATE"` `businessObject="Workspace"`
- `displayName="Retrieve workspaces"` `action="RETRIEVEALL"` `businessObject="Workspace"`
- `displayName="Retrieve workspace"` `action="RETRIEVE"` `businessObject="Workspace"`
- `displayName="Delete workspace"` `action="DELETEALL"` `businessObject="Workspace"`
- `displayName="Retrieve workspace users"` `action="RETRIEVEALL"` `businessObject="WorkspaceUser"`
- `displayName="Retrieve admin workspaces"` `action="RETRIEVEALL"` `businessObject="AdminWorkspace"`
- `displayName="Retrieve admin workspace users"` `action="RETRIEVEALL"` `businessObject="AdminWorkspaceUser"`
- `displayName="Retrieve datasets"` `action="RETRIEVEALL"` `businessObject="Dataset"`
- `displayName="Retrieve dataset"` `action="RETRIEVE"` `businessObject="Dataset"`
- `displayName="Update dataset"` `action="UPDATEALL"` `businessObject="Dataset"`
- `displayName="Delete dataset"` `action="DELETEALL"` `businessObject="Dataset"`
- `displayName="Retrieve dataset access users"` `action="RETRIEVEALL"` `businessObject="DatasetAccessUser"`
- `displayName="Retrieve dataset gateways"` `action="RETRIEVEALL"` `businessObject="DatasetGateway"`
- `displayName="Retrieve dataset data sources"` `action="RETRIEVEALL"` `businessObject="DatasetDataSource"`
- `displayName="Update dataset data source"` `action="UPDATEALL"` `businessObject="DatasetDataSource"`
- `displayName="Retrieve dataset parameters"` `action="RETRIEVEALL"` `businessObject="DatasetParameter"`
- `displayName="Update dataset parameter"` `action="UPDATEALL"` `businessObject="DatasetParameter"`
- `displayName="Retrieve direct query refresh schedules"` `action="RETRIEVEALL"` `businessObject="DirectQueryRefreshSchedule"`
- `displayName="Update direct query refresh schedule"` `action="UPDATEALL"` `businessObject="DirectQueryRefreshSchedule"`
- `displayName="Retrieve dataset refresh details"` `action="RETRIEVEALL"` `businessObject="DatasetRefreshDetail"`
- `displayName="Retrieve refresh schedules"` `action="RETRIEVEALL"` `businessObject="RefreshSchedule"`
- `displayName="Update refresh schedule"` `action="UPDATEALL"` `businessObject="RefreshSchedule"`
- `displayName="Retrieve refresh histories"` `action="RETRIEVEALL"` `businessObject="RefreshHistory"`
- `displayName="Create push dataset"` `action="CREATE"` `businessObject="PushDataset"`
- `displayName="Retrieve tables"` `action="RETRIEVEALL"` `businessObject="Table"`
- `displayName="Update table"` `action="UPDATEALL"` `businessObject="Table"`
- `displayName="Retrieve dataflows"` `action="RETRIEVEALL"` `businessObject="Dataflow"`
- `displayName="Retrieve dataflow"` `action="RETRIEVE"` `businessObject="Dataflow"`
- `displayName="Update dataflow"` `action="UPDATEALL"` `businessObject="Dataflow"`
- `displayName="Delete dataflow"` `action="DELETEALL"` `businessObject="Dataflow"`
- `displayName="Retrieve dataflow data sources"` `action="RETRIEVEALL"` `businessObject="DataflowDataSource"`
- `displayName="Retrieve reports"` `action="RETRIEVEALL"` `businessObject="Report"`
- `displayName="Retrieve report"` `action="RETRIEVE"` `businessObject="Report"`
- `displayName="Update report"` `action="UPDATEALL"` `businessObject="Report"`
- `displayName="Delete report"` `action="DELETEALL"` `businessObject="Report"`
- `displayName="Retrieve gateways"` `action="RETRIEVEALL"` `businessObject="Gateway"`
- `displayName="Retrieve gateway data sources"` `action="RETRIEVEALL"` `businessObject="GatewayDataSource"`
- `displayName="Delete gateway data source"` `action="DELETEALL"` `businessObject="GatewayDataSource"`
- `displayName="Create scorecard"` `action="CREATE"` `businessObject="Scorecard"`
- `displayName="Retrieve scorecards"` `action="RETRIEVEALL"` `businessObject="Scorecard"`
- `displayName="Retrieve scorecard"` `action="RETRIEVE"` `businessObject="Scorecard"`
- `displayName="Update scorecard"` `action="UPDATEALL"` `businessObject="Scorecard"`
- `displayName="Delete scorecard"` `action="DELETEALL"` `businessObject="Scorecard"`
- `displayName="Create goal"` `action="CREATE"` `businessObject="Goal"`
- `displayName="Retrieve goals"` `action="RETRIEVEALL"` `businessObject="Goal"`
- `displayName="Retrieve goal"` `action="RETRIEVE"` `businessObject="Goal"`
- `displayName="Update goal"` `action="UPDATEALL"` `businessObject="Goal"`
- `displayName="Delete goal"` `action="DELETEALL"` `businessObject="Goal"`
- `displayName="Create goal note"` `action="CREATE"` `businessObject="GoalNote"`
- `displayName="Update goal note"` `action="UPDATEALL"` `businessObject="GoalNote"`
- `displayName="Delete goal note"` `action="DELETEALL"` `businessObject="GoalNote"`
- `displayName="Create goal status rule"` `action="CREATE"` `businessObject="GoalStatusRule"`
- `displayName="Retrieve goal status rules"` `action="RETRIEVEALL"` `businessObject="GoalStatusRule"`
- `displayName="Retrieve goal status rule"` `action="RETRIEVE"` `businessObject="GoalStatusRule"`
- `displayName="Delete goal status rule"` `action="DELETEALL"` `businessObject="GoalStatusRule"`
- `displayName="Create goal value"` `action="CREATE"` `businessObject="GoalValue"`
- `displayName="Retrieve goal values"` `action="RETRIEVEALL"` `businessObject="GoalValue"`
- `displayName="Retrieve goal value"` `action="RETRIEVE"` `businessObject="GoalValue"`
- `displayName="Update goal value"` `action="UPDATEALL"` `businessObject="GoalValue"`
- `displayName="Delete goal value"` `action="DELETEALL"` `businessObject="GoalValue"`
- `displayName="Retrieve imports"` `action="RETRIEVEALL"` `businessObject="Import"`
- `displayName="Retrieve import"` `action="RETRIEVE"` `businessObject="Import"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSPowerBI1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSPowerBI1" policyTemplate="admin_v1_basic_oauth" policyType="mspowerbi" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>admin</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <tenantId/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
