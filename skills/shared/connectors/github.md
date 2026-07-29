# GitHub

## Purpose
Connector-specific rules for GitHub Request and GitHub Input nodes.

## When to use
Use this document when the requested ACE flow includes a GitHub Request node or GitHub Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- GitHub Request node
- GitHub Input node

## Required node attributes
### GitHub Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_github.msgnode`
- `applicationConnectorType="github"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### GitHub Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_github.msgnode`
- `applicationConnectorType="github"`

## Schema file requirements
For GitHub Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for GitHub Request nodes:

- `displayName="Retrieve organizations"` `action="RETRIEVEALL"` `businessObject="Organization"`
- `displayName="Update organization"` `action="UPDATEALL"` `businessObject="Organization"`
- `displayName="Create repository"` `action="CREATE"` `businessObject="Repository"`
- `displayName="Retrieve repositories"` `action="RETRIEVEALL"` `businessObject="Repository"`
- `displayName="Update repository"` `action="UPDATEALL"` `businessObject="Repository"`
- `displayName="Delete repository"` `action="DELETEALL"` `businessObject="Repository"`
- `displayName="Create issue"` `action="CREATE"` `businessObject="Issue"`
- `displayName="Retrieve issues"` `action="RETRIEVEALL"` `businessObject="Issue"`
- `displayName="Update issue"` `action="UPDATEALL"` `businessObject="Issue"`
- `displayName="Add assignees"` `action="ADDASSIGNEES"` `businessObject="Issue"`
- `displayName="Remove assignees"` `action="REMOVEASSIGNEES"` `businessObject="Issue"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comment"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="Comment"`
- `displayName="Update comment"` `action="UPDATEALL"` `businessObject="Comment"`
- `displayName="Delete comment"` `action="DELETEALL"` `businessObject="Comment"`
- `displayName="Create pull request"` `action="CREATE"` `businessObject="Pullrequest"`
- `displayName="Retrieve pull requests"` `action="RETRIEVEALL"` `businessObject="Pullrequest"`
- `displayName="Update pull request"` `action="UPDATEALL"` `businessObject="Pullrequest"`
- `displayName="Merge pull request"` `action="MERGEPULLREQUEST"` `businessObject="Pullrequest"`
- `displayName="Create review comment"` `action="CREATE"` `businessObject="Reviewcomment"`
- `displayName="Retrieve review comments"` `action="RETRIEVEALL"` `businessObject="Reviewcomment"`
- `displayName="Update review comment"` `action="UPDATEALL"` `businessObject="Reviewcomment"`
- `displayName="Delete review comment"` `action="DELETEALL"` `businessObject="Reviewcomment"`
- `displayName="Reply review comment"` `action="REPLYREVIEWCOMMENT"` `businessObject="Reviewcomment"`
- `displayName="Create review"` `action="CREATE"` `businessObject="Review"`
- `displayName="Retrieve reviews"` `action="RETRIEVEALL"` `businessObject="Review"`
- `displayName="Update review"` `action="UPDATEALL"` `businessObject="Review"`
- `displayName="Delete review"` `action="DELETEALL"` `businessObject="Review"`
- `displayName="Submit review"` `action="SUBMITREVIEW"` `businessObject="Review"`
- `displayName="Request review"` `action="REQUESTREVIEWERS"` `businessObject="Reviewrequest"`
- `displayName="Retrieve branches"` `action="RETRIEVEALL"` `businessObject="Branch"`
- `displayName="Merge branch"` `action="MERGEBRANCH"` `businessObject="Branch"`
- `displayName="Retrieve commits"` `action="RETRIEVEALL"` `businessObject="Commit"`
- `displayName="Create commit comment"` `action="CREATE"` `businessObject="Commitcomment"`
- `displayName="Retrieve commit comments"` `action="RETRIEVEALL"` `businessObject="Commitcomment"`
- `displayName="Update commit comment"` `action="UPDATEALL"` `businessObject="Commitcomment"`
- `displayName="Delete commit comment"` `action="DELETEALL"` `businessObject="Commitcomment"`
- `displayName="Create team"` `action="CREATE"` `businessObject="Team"`
- `displayName="Retrieve teams"` `action="RETRIEVEALL"` `businessObject="Team"`
- `displayName="Update team"` `action="UPDATEALL"` `businessObject="Team"`
- `displayName="Delete team"` `action="DELETEALL"` `businessObject="Team"`
- `displayName="Add or update team member"` `action="ADDUPDATEMEMBERSHIP"` `businessObject="Team"`
- `displayName="Remove team member"` `action="REMOVEMEMBERSHIP"` `businessObject="Team"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve collaborators"` `action="RETRIEVEALL"` `businessObject="Collaborator"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:GitHub1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="GitHub1" policyTemplate="online_v1_basic" policyType="github" shortDescription="" version="">
     <credentialName>GitHubCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
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
