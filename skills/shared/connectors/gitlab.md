# GitLab

## Purpose
Connector-specific rules for GitLab Request and GitLab Input nodes.

## When to use
Use this document when the requested ACE flow includes a GitLab Request node or GitLab Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- GitLab Request node
- GitLab Input node

## Required node attributes
### GitLab Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_gitlab.msgnode`
- `applicationConnectorType="gitlab"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### GitLab Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_gitlab.msgnode`
- `applicationConnectorType="gitlab"`

## Schema file requirements
For GitLab Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for GitLab Request nodes:

- `displayName="Create project"` `action="CREATE"` `businessObject="Project"`
- `displayName="Retrieve projects"` `action="RETRIEVEALL"` `businessObject="Project"`
- `displayName="Update project"` `action="UPDATEALL"` `businessObject="Project"`
- `displayName="Delete project"` `action="DELETEALL"` `businessObject="Project"`
- `displayName="Share project with group"` `action="SHAREPROJECTWITHGROUP"` `businessObject="Project"`
- `displayName="Create group"` `action="CREATE"` `businessObject="Group"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Update group"` `action="UPDATEALL"` `businessObject="Group"`
- `displayName="Delete group"` `action="DELETEALL"` `businessObject="Group"`
- `displayName="Create issue"` `action="CREATE"` `businessObject="Issue"`
- `displayName="Retrieve issues"` `action="RETRIEVEALL"` `businessObject="Issue"`
- `displayName="Update issue"` `action="UPDATEALL"` `businessObject="Issue"`
- `displayName="Delete issue"` `action="DELETEALL"` `businessObject="Issue"`
- `displayName="Move issue"` `action="MOVEANISSUE"` `businessObject="Issue"`
- `displayName="Retrieve namespaces"` `action="RETRIEVEALL"` `businessObject="Namespace"`
- `displayName="Retrieve commits"` `action="RETRIEVEALL"` `businessObject="Commit"`
- `displayName="Revert a commit"` `action="REVERTACOMMIT"` `businessObject="Commit"`
- `displayName="Create branch"` `action="CREATE"` `businessObject="Branch"`
- `displayName="Retrieve branches"` `action="RETRIEVEALL"` `businessObject="Branch"`
- `displayName="Delete branch"` `action="DELETEALL"` `businessObject="Branch"`
- `displayName="Create merge request"` `action="CREATE"` `businessObject="MergeRequest"`
- `displayName="Retrieve merge requests"` `action="RETRIEVEALL"` `businessObject="MergeRequest"`
- `displayName="Update merge request"` `action="UPDATEALL"` `businessObject="MergeRequest"`
- `displayName="Delete merge request"` `action="DELETEALL"` `businessObject="MergeRequest"`
- `displayName="Accept merge request"` `action="ACCEPTMERGEREQUEST"` `businessObject="MergeRequest"`
- `displayName="Create milestone"` `action="CREATE"` `businessObject="Milestone"`
- `displayName="Retrieve milestones"` `action="RETRIEVEALL"` `businessObject="Milestone"`
- `displayName="Update milestone"` `action="UPDATEALL"` `businessObject="Milestone"`
- `displayName="Delete milestone"` `action="DELETEALL"` `businessObject="Milestone"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve jobs"` `action="RETRIEVEALL"` `businessObject="Job"`
- `displayName="Retry job"` `action="RETRYAJOB"` `businessObject="Job"`
- `displayName="Cancel job"` `action="CANCELAJOB"` `businessObject="Job"`
- `displayName="Erase job"` `action="ERASEAJOB"` `businessObject="Job"`
- `displayName="Download job artifacts"` `action="DOWNLOADJOBARTIFACTS"` `businessObject="Job"`
- `displayName="Create label"` `action="CREATE"` `businessObject="Label"`
- `displayName="Retrieve labels"` `action="RETRIEVEALL"` `businessObject="Label"`
- `displayName="Update label"` `action="UPDATEALL"` `businessObject="Label"`
- `displayName="Delete label"` `action="DELETEALL"` `businessObject="Label"`
- `displayName="Create tag"` `action="CREATE"` `businessObject="Tag"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="Tag"`
- `displayName="Delete tag"` `action="DELETEALL"` `businessObject="Tag"`
- `displayName="Create release"` `action="CREATE"` `businessObject="Release"`
- `displayName="Retrieve releases"` `action="RETRIEVEALL"` `businessObject="Release"`
- `displayName="Update release"` `action="UPDATEALL"` `businessObject="Release"`
- `displayName="Delete release"` `action="DELETEALL"` `businessObject="Release"`
- `displayName="Create pipeline"` `action="CREATE"` `businessObject="Pipeline"`
- `displayName="Retrieve pipelines"` `action="RETRIEVEALL"` `businessObject="Pipeline"`
- `displayName="Delete pipeline"` `action="DELETEALL"` `businessObject="Pipeline"`
- `displayName="Retry jobs in a pipeline"` `action="RETRYJOBSINAPIPELINE"` `businessObject="Pipeline"`
- `displayName="Cancel a pipeline jobs"` `action="CANCELAPIPELINEJOBS"` `businessObject="Pipeline"`
- `displayName="Retrieve members"` `action="RETRIEVEALL"` `businessObject="Member"`
- `displayName="Add member"` `action="ADDMEMBER"` `businessObject="Member"`
- `displayName="Edit member"` `action="EDITMEMBER"` `businessObject="Member"`
- `displayName="Remove member"` `action="REMOVEMEMBER"` `businessObject="Member"`
- `displayName="Create issue note"` `action="CREATE"` `businessObject="IssueNote"`
- `displayName="Retrieve issue notes"` `action="RETRIEVEALL"` `businessObject="IssueNote"`
- `displayName="Update issue note"` `action="UPDATEALL"` `businessObject="IssueNote"`
- `displayName="Delete issue note"` `action="DELETEALL"` `businessObject="IssueNote"`
- `displayName="Create merge request note"` `action="CREATE"` `businessObject="MergeRequestNote"`
- `displayName="Retrieve merge request notes"` `action="RETRIEVEALL"` `businessObject="MergeRequestNote"`
- `displayName="Update merge request note"` `action="UPDATEALL"` `businessObject="MergeRequestNote"`
- `displayName="Delete merge request note"` `action="DELETEALL"` `businessObject="MergeRequestNote"`
- `displayName="Create epic"` `action="CREATE"` `businessObject="Epic"`
- `displayName="Retrieve epics"` `action="RETRIEVEALL"` `businessObject="Epic"`
- `displayName="Update epic"` `action="UPDATEALL"` `businessObject="Epic"`
- `displayName="Delete epic"` `action="DELETEALL"` `businessObject="Epic"`
- `displayName="Create epic note"` `action="CREATE"` `businessObject="EpicNote"`
- `displayName="Retrieve epic notes"` `action="RETRIEVEALL"` `businessObject="EpicNote"`
- `displayName="Update epic note"` `action="UPDATEALL"` `businessObject="EpicNote"`
- `displayName="Delete epic note"` `action="DELETEALL"` `businessObject="EpicNote"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:GitLab1`.

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
