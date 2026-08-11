# Microsoft Azure DevOps

## Purpose
Connector-specific rules for Microsoft Azure DevOps Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft Azure DevOps Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft Azure DevOps Request node

## Required node attributes
### Microsoft Azure DevOps Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_azuredevops.msgnode`
- `applicationConnectorType="azuredevops"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft Azure DevOps Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft Azure DevOps Request nodes:

- `displayName="Retrieve artifacts"` `action="RETRIEVEALL"` `businessObject="Artifact"`
- `displayName="Create branch"` `action="CREATE"` `businessObject="Branch"`
- `displayName="Retrieve branches"` `action="RETRIEVEALL"` `businessObject="Branch"`
- `displayName="Update branch"` `action="UPDATEALL"` `businessObject="Branch"`
- `displayName="Delete branch"` `action="DELETEALL"` `businessObject="Branch"`
- `displayName="Retrieve commits"` `action="RETRIEVEALL"` `businessObject="Commit"`
- `displayName="Retrieve commit"` `action="RETRIEVE"` `businessObject="Commit"`
- `displayName="Retrieve feeds"` `action="RETRIEVEALL"` `businessObject="Feed"`
- `displayName="Retrieve organizations"` `action="RETRIEVEALL"` `businessObject="Organization"`
- `displayName="Retrieve pipelines"` `action="RETRIEVEALL"` `businessObject="Pipeline"`
- `displayName="Run pipeline"` `action="RUNPIPELINE"` `businessObject="Pipeline"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Project"`
- `displayName="Create pull request"` `action="CREATE"` `businessObject="PullRequest"`
- `displayName="Retrieve pull requests"` `action="RETRIEVEALL"` `businessObject="PullRequest"`
- `displayName="Retrieve pull request"` `action="RETRIEVE"` `businessObject="PullRequest"`
- `displayName="Update pull request"` `action="UPDATEALL"` `businessObject="PullRequest"`
- `displayName="Create pull request thread"` `action="CREATE"` `businessObject="PullRequestThread"`
- `displayName="Retrieve pull request threads"` `action="RETRIEVEALL"` `businessObject="PullRequestThread"`
- `displayName="Retrieve pull request thread"` `action="RETRIEVE"` `businessObject="PullRequestThread"`
- `displayName="Update pull request thread"` `action="UPDATEALL"` `businessObject="PullRequestThread"`
- `displayName="Create pull request thread comment"` `action="CREATE"` `businessObject="PullRequestThreadComment"`
- `displayName="Retrieve pull request thread comments"` `action="RETRIEVEALL"` `businessObject="PullRequestThreadComment"`
- `displayName="Retrieve pull request thread comment"` `action="RETRIEVE"` `businessObject="PullRequestThreadComment"`
- `displayName="Update pull request thread comment"` `action="UPDATEALL"` `businessObject="PullRequestThreadComment"`
- `displayName="Delete pull request thread comment"` `action="DELETEALL"` `businessObject="PullRequestThreadComment"`
- `displayName="Create push"` `action="CREATE"` `businessObject="Push"`
- `displayName="Retrieve pushes"` `action="RETRIEVEALL"` `businessObject="Push"`
- `displayName="Retrieve push"` `action="RETRIEVE"` `businessObject="Push"`
- `displayName="Create repository"` `action="CREATE"` `businessObject="Repository"`
- `displayName="Retrieve repositories"` `action="RETRIEVEALL"` `businessObject="Repository"`
- `displayName="Retrieve repository"` `action="RETRIEVE"` `businessObject="Repository"`
- `displayName="Update repository"` `action="UPDATEALL"` `businessObject="Repository"`
- `displayName="Delete repository"` `action="DELETEALL"` `businessObject="Repository"`
- `displayName="Create work item"` `action="CREATE"` `businessObject="WorkItem"`
- `displayName="Retrieve work items"` `action="RETRIEVEALL"` `businessObject="WorkItem"`
- `displayName="Retrieve work item"` `action="RETRIEVE"` `businessObject="WorkItem"`
- `displayName="Update work item"` `action="UPDATEALL"` `businessObject="WorkItem"`
- `displayName="Delete work item"` `action="DELETEALL"` `businessObject="WorkItem"`
- `displayName="Create work item comment"` `action="CREATE"` `businessObject="WorkItemComment"`
- `displayName="Retrieve work item comments"` `action="RETRIEVEALL"` `businessObject="WorkItemComment"`
- `displayName="Retrieve work item comment"` `action="RETRIEVE"` `businessObject="WorkItemComment"`
- `displayName="Update work item comment"` `action="UPDATEALL"` `businessObject="WorkItemComment"`
- `displayName="Delete work item comment"` `action="DELETEALL"` `businessObject="WorkItemComment"`
- `displayName="Retrieve work item types"` `action="RETRIEVEALL"` `businessObject="WorkItemType"`
- `displayName="Retrieve work item type"` `action="RETRIEVE"` `businessObject="WorkItemType"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AzureDevOps1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="AzureDevOps1" policyTemplate="online_v1_oauth2_credentials" policyType="azuredevops" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_CREDENTIALS</authenticationMethod>
        <apiUrl>https://dev.azure.com</apiUrl>
        <tenantId/>
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
