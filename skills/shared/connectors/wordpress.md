# WordPress

## Purpose
Connector-specific rules for WordPress Request nodes.

## When to use
Use this document when the requested ACE flow includes a WordPress Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- WordPress Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_wordpress.msgnode`
- `applicationConnectorType="wordpress"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For WordPress Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for WordPress Request nodes:

- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Create post"` `action="CREATE"` `businessObject="Post"`
- `displayName="Retrieve posts"` `action="RETRIEVEALL"` `businessObject="Post"`
- `displayName="Create category"` `action="CREATE"` `businessObject="Category"`
- `displayName="Retrieve categories"` `action="RETRIEVEALL"` `businessObject="Category"`
- `displayName="Create tag"` `action="CREATE"` `businessObject="Tag"`
- `displayName="Retrieve tags"` `action="RETRIEVEALL"` `businessObject="Tag"`
- `displayName="Retrieve media"` `action="RETRIEVEALL"` `businessObject="Media"`
- `displayName="Follow blog"` `action="FOLLOWBLOG"` `businessObject="Follower"`
- `displayName="Unfollow blog"` `action="UNFOLLOWBLOG"` `businessObject="Follower"`
- `displayName="Retrieve sites"` `action="RETRIEVEALL"` `businessObject="Site"`
- `displayName="Create comment"` `action="CREATE"` `businessObject="Comment"`
- `displayName="Retrieve comments"` `action="RETRIEVEALL"` `businessObject="Comment"`
- `displayName="Retrieve feed details"` `action="GETFEEDDETAILS"` `businessObject="Feed"`
- `displayName="Retrieve followed feeds"` `action="GETFOLLOWINGFEEDS"` `businessObject="Feed"`
- `displayName="Retrieve recommended blogs"` `action="RETRIEVEALL"` `businessObject="Blog"`
- `displayName="Subscribe to tag"` `action="SUBSCRIBETAG"` `businessObject="TagDetails"`
- `displayName="Retrieve subscribed tags"` `action="GETSUBSCRIBEDTAGS"` `businessObject="TagDetails"`
- `displayName="Unsubscribe from tag"` `action="UNSUBSCRIBETAG"` `businessObject="TagDetails"`
- `displayName="Retrieve subscribed status for tag"` `action="GETTAGSUBSCRIBEDSTATUS"` `businessObject="TagDetails"`
- `displayName="Retrieve most commented posts for site"` `action="RETRIEVEALL"` `businessObject="PostStats"`
- `displayName="Retrieve view stats for post"` `action="RETRIEVEALL"` `businessObject="PostViews"`
- `displayName="Retrieve stats for site"` `action="RETRIEVEALL"` `businessObject="SiteStats"`
- `displayName="Retrieve publicize follower count for site"` `action="RETRIEVEALL"` `businessObject="SitePublicizeFollowers"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Wordpress1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Wordpress1" policyTemplate="online_v1_basic_oauth" policyType="wordpress" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
