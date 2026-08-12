# IBM The Weather Company

## Purpose
Connector-specific rules for IBM The Weather Company Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM The Weather Company Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM The Weather Company Request node

## Required node attributes
### IBM The Weather Company Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ibmtwc.msgnode`
- `applicationConnectorType="ibmtwc"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM The Weather Company Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM The Weather Company Request nodes:

- `displayName="Retrieve historical observations"` `action="RETRIEVEALL"` `businessObject="HistoricalObservation"`
- `displayName="Get forecast"` `action="GETFORECAST"` `businessObject="Forecast"`
- `displayName="Get near locations"` `action="GETNEARLOCATION"` `businessObject="NearLocation"`
- `displayName="Get locations"` `action="GETLOCATION"` `businessObject="Location"`
- `displayName="Get locations by point"` `action="GETLOCATIONBYPOINT"` `businessObject="LocationByPoint"`
- `displayName="Get current conditions"` `action="GETCURRENTCONDITIONS"` `businessObject="CurrentCondition"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:IbmTwc1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="IbmTwc1" policyTemplate="online_v1_basic" policyType="ibmtwc" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
