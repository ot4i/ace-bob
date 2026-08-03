# Google Universal Analytics

## Purpose
Connector-specific rules for Google Universal Analytics Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Universal Analytics Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Universal Analytics Request node

## Note on deprecation
This connector is **deprecated**. It targets the Google Universal Analytics v3 Management API and Core Reporting API. For new flows, use the Google Analytics 4 connector (`applicationConnectorType="googleanalytics4"`) documented in [`googleanalytics.md`](../googleanalytics.md).

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googleanalytics.msgnode`
- `applicationConnectorType="googleanalytics"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Universal Analytics Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Google Universal Analytics Request nodes:

- `displayName="Retrieve account summaries"` `action="RETRIEVEALL"` `businessObject="accountSummaries"`
- `displayName="Count account summaries"` `action="COUNT"` `businessObject="accountSummaries"`
- `displayName="Retrieve account user links"` `action="RETRIEVEALL"` `businessObject="accountUserLinks"`
- `displayName="Count account user links"` `action="COUNT"` `businessObject="accountUserLinks"`
- `displayName="Retrieve accounts"` `action="RETRIEVEALL"` `businessObject="accounts"`
- `displayName="Count accounts"` `action="COUNT"` `businessObject="accounts"`
- `displayName="Retrieve custom data sources"` `action="RETRIEVEALL"` `businessObject="customDataSources"`
- `displayName="Count custom data sources"` `action="COUNT"` `businessObject="customDataSources"`
- `displayName="Retrieve custom dimensions"` `action="RETRIEVEALL"` `businessObject="customDimensions"`
- `displayName="Count custom dimensions"` `action="COUNT"` `businessObject="customDimensions"`
- `displayName="Retrieve custom metrics"` `action="RETRIEVEALL"` `businessObject="customMetrics"`
- `displayName="Count custom metrics"` `action="COUNT"` `businessObject="customMetrics"`
- `displayName="Retrieve filters"` `action="RETRIEVEALL"` `businessObject="filters"`
- `displayName="Count filters"` `action="COUNT"` `businessObject="filters"`
- `displayName="Retrieve goals"` `action="RETRIEVEALL"` `businessObject="goals"`
- `displayName="Count goals"` `action="COUNT"` `businessObject="goals"`
- `displayName="Retrieve profile filter links"` `action="RETRIEVEALL"` `businessObject="profileFilterLinks"`
- `displayName="Count profile filter links"` `action="COUNT"` `businessObject="profileFilterLinks"`
- `displayName="Retrieve profile user links"` `action="RETRIEVEALL"` `businessObject="profileUserLinks"`
- `displayName="Count profile user links"` `action="COUNT"` `businessObject="profileUserLinks"`
- `displayName="Retrieve profiles"` `action="RETRIEVEALL"` `businessObject="profiles"`
- `displayName="Count profiles"` `action="COUNT"` `businessObject="profiles"`
- `displayName="Retrieve segments"` `action="RETRIEVEALL"` `businessObject="segments"`
- `displayName="Count segments"` `action="COUNT"` `businessObject="segments"`
- `displayName="Retrieve web properties"` `action="RETRIEVEALL"` `businessObject="webproperties"`
- `displayName="Count web properties"` `action="COUNT"` `businessObject="webproperties"`
- `displayName="Generate core reports"` `action="GENERATECOREREPORTS"` `businessObject="reports"`
- `displayName="Get multi-channel funnel report"` `action="GETMCFREPORT"` `businessObject="mcf"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googleuniversalanalytics`.
- The policy file is available at `EveryPolicy/googleuniversalanalytics.policyxml`.
- Note: the policy uses `policyType="googleanalytics"` (not `googleuniversalanalytics`) and `policyName="googleuniversalanalytics"`. It uses `authenticationMethod="BASIC_OAUTH"` and does not include a `<proxyId/>` or `<apiUrl/>` field.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googleuniversalanalytics" policyTemplate="online_v1_basic_oauth" policyType="googleanalytics" shortDescription="" version="">
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
- [`loopback-connector-googleanalytics/descriptors/googleanalytics.json`](../loopback-connector-googleanalytics/descriptors/googleanalytics.json)
- [`loopback-connector-googleanalytics/descriptors/googleanalytics.yaml`](../loopback-connector-googleanalytics/descriptors/googleanalytics.yaml)
- [`loopback-connector-googleanalytics/lib/constants/gaConstants.json`](../loopback-connector-googleanalytics/lib/constants/gaConstants.json)
- [`loopback-connector-googleanalytics/lib/constants/metadata.json`](../loopback-connector-googleanalytics/lib/constants/metadata.json)
- [`appconnect-connector-googleanalytics/lib/openapi/connector.json`](../appconnect-connector-googleanalytics/lib/openapi/connector.json)
- [`EveryPolicy/googleuniversalanalytics.policyxml`](../EveryPolicy/googleuniversalanalytics.policyxml)
