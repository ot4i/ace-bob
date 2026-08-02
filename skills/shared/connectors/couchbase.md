# Couchbase

## Purpose
Connector-specific rules for Couchbase Request nodes.

## When to use
Use this document when the requested ACE flow includes a Couchbase Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Couchbase Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_couchbase.msgnode`
- `applicationConnectorType="couchbase"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Couchbase Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Couchbase Request nodes:

- `displayName="Retrieve buckets"` `action="RETRIEVEALL"` `businessObject="Bucket"`
- `displayName="Retrieve collections"` `action="RETRIEVEALL"` `businessObject="Collection"`
- `displayName="Retrieve scopes"` `action="RETRIEVEALL"` `businessObject="Scope"`
- `displayName="Create document"` `action="CREATE"` `businessObject="Document"`
- `displayName="Retrieve documents"` `action="RETRIEVEALL"` `businessObject="Document"`
- `displayName="Update document"` `action="UPDATEALL"` `businessObject="Document"`
- `displayName="Delete documents"` `action="DELETEALL"` `businessObject="Document"`
- `displayName="Update or create document"` `action="UPSERTWITHWHERE"` `businessObject="Document"`
- `displayName="Execute custom SQL"` `action="EXECUTECUSTOMSQL"` `businessObject="Customsql"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Couchbase1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Couchbase1" policyTemplate="onprem_v1_basic" policyType="couchbase" shortDescription="" version="">
        <credentialName>CouchbaseCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>onprem</applicationType>
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
