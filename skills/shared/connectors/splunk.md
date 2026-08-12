# Splunk

## Purpose
Connector-specific rules for Splunk Request nodes.

## When to use
Use this document when the requested ACE flow includes a Splunk Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Splunk Request node

## Connector type
Splunk is a **dynamic (OpenAPI-based)** connector. It does not use the legacy `xmi:type` / `applicationConnectorType` attributes. The connector is implemented in [`appconnect-connector-splunk`](../appconnect-connector-splunk/) and exposes its operations via the OpenAPI specification at [`lib/openapi/connector.json`](../appconnect-connector-splunk/lib/openapi/connector.json).

## Schema file requirements
For Splunk Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Splunk Request nodes:

- `summary="Retrieve all applications"` `action="retrievewithwhere"` `model="Applications"`
- `summary="Retrieve HEC token by ID"` `action="retrievewithwhere"` `model="HTTP Event Collector (HEC)"`
- `summary="Retrieve HEC token"` `action="retrievewithwhere"` `model="HTTP Event Collector (HEC)"`
- `summary="Send HEC data"` `action="create"` `model="HTTP Event Collector (HEC)"`
- `summary="Retrieve all users"` `action="retrievewithwhere"` `model="Users"`
- `summary="Create search job"` `action="upsertwithwhere"` `model="Search"`
- `summary="Retrieve searches by ID"` `action="retrievewithwhere"` `model="Search"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Splunk1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Splunk1" policyTemplate="online_v1_basic" policyType="splunk" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
        <tokenUrl/>
        <acceptSelfSignedCerts>false</acceptSelfSignedCerts>
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
