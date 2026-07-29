# Redis

## Purpose
Connector-specific rules for Redis Request nodes.

## When to use
Use this document when the requested ACE flow includes a Redis Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Redis Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_rediscache.msgnode`
- `applicationConnectorType="rediscache"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Redis Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Redis Request nodes:

- `displayName="Delete key"` `action="DELETEALL"` `businessObject="Key"`
- `displayName="Retrieve keys"` `action="RETRIEVEKEYS"` `businessObject="Key"`
- `displayName="Check key presence"` `action="CHECKKEYPRESENCE"` `businessObject="Key"`
- `displayName="Get data type of key"` `action="GETDATATYPEOFKEY"` `businessObject="Key"`
- `displayName="Set expire timeout (seconds/milliseconds)"` `action="SETEXPIRETIMEOUT"` `businessObject="Key"`
- `displayName="Set expire at time"` `action="SETEXPIREATTIME"` `businessObject="Key"`
- `displayName="Get time to live"` `action="GETTIMETOLIVE"` `businessObject="Key"`
- `displayName="Remove expire timeout on key"` `action="REMOVEEXPIRETIMEOUTONKEY"` `businessObject="Key"`
- `displayName="Rename key"` `action="RENAMEKEY"` `businessObject="Key"`
- `displayName="Update or create string"` `action="UPSERTWITHWHERE"` `businessObject="String"`
- `displayName="Append a value to string"` `action="APPENDVALUETOSTRING"` `businessObject="String"`
- `displayName="Get value"` `action="GETVALUE"` `businessObject="String"`
- `displayName="Update or create hash"` `action="UPSERTWITHWHERE"` `businessObject="Hash"`
- `displayName="Delete hash field"` `action="DELETEALL"` `businessObject="Hash"`
- `displayName="Check hash field presence"` `action="CHECKFIELDPRESENCE"` `businessObject="Hash"`
- `displayName="Get hash field count"` `action="GETFIELDCOUNT"` `businessObject="Hash"`
- `displayName="Get hash field value"` `action="GETFIELDVALUE"` `businessObject="Hash"`
- `displayName="Update or create set"` `action="UPSERTWITHWHERE"` `businessObject="Set"`
- `displayName="Delete set member"` `action="DELETEALL"` `businessObject="Set"`
- `displayName="Check set member presence"` `action="CHECKMEMBERPRESENCE"` `businessObject="Set"`
- `displayName="Get set member count"` `action="GETMEMBERCOUNT"` `businessObject="Set"`
- `displayName="Retrieve set members"` `action="RETRIEVEALLMEMBERS"` `businessObject="Set"`
- `displayName="Update or create list"` `action="UPSERTWITHWHERE"` `businessObject="List"`
- `displayName="Update list"` `action="UPDATEALL"` `businessObject="List"`
- `displayName="Delete list element"` `action="DELETEALL"` `businessObject="List"`
- `displayName="Get list length"` `action="GETLISTLENGTH"` `businessObject="List"`
- `displayName="Trim the list"` `action="TRIMTHELIST"` `businessObject="List"`
- `displayName="Retrieve list elements"` `action="RETRIEVEELEMENT"` `businessObject="List"`
- `displayName="Update or create sorted set"` `action="UPSERTWITHWHERE"` `businessObject="SortedSet"`
- `displayName="Delete sorted set member"` `action="DELETEALL"` `businessObject="SortedSet"`
- `displayName="Get sorted set member count"` `action="GETSORTEDSETMEMBERCOUNT"` `businessObject="SortedSet"`
- `displayName="Get member count by score range"` `action="GETMEMBERCOUNTBYSCORERANGE"` `businessObject="SortedSet"`
- `displayName="Get sorted set member rank"` `action="GETMEMBERRANK"` `businessObject="SortedSet"`
- `displayName="Get sorted set member score"` `action="GETMEMBERSCORE"` `businessObject="SortedSet"`
- `displayName="Retrieve sorted set members"` `action="RETRIEVEMEMBER"` `businessObject="SortedSet"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Redis1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Redis1" policyTemplate="RedisConnection" policyType="RedisConnection" shortDescription="" version="">
     <hostname>localhost</hostname>
     <port>6379</port>
     <databaseNumber>0</databaseNumber>
     <clientName/>
     <securityIdentity>RedisCredential</securityIdentity>
     <useSSL>false</useSSL>
     <sslProtocol>TLSv1.3</sslProtocol>
     <sslRejectUnauthorized>true</sslRejectUnauthorized>
     <maximumConnectionCount>8</maximumConnectionCount>
     <maximumIdleConnectionCount>8</maximumIdleConnectionCount>
     <maximumIdleConnectionAge>60</maximumIdleConnectionAge>
     <connectionTimeoutSecs>2</connectionTimeoutSecs>
     <commandTimeoutSecs>120</commandTimeoutSecs>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
