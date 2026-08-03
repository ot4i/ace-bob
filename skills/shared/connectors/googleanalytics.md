# Google Analytics

## Purpose
Connector-specific rules for Google Analytics Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Analytics Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Analytics Request node

## Note on connector versions
There are two distinct Google Analytics connector variants, each with a separate policy type:

- **Google Universal Analytics** (`policyType="googleanalytics"`) — the loopback-based connector (`loopback-connector-googleanalytics`). This connector is **deprecated**. Use the policy file `EveryPolicy/googleuniversalanalytics.policyxml`.
- **Google Analytics 4** (`policyType="googleanalytics4"`) — the appconnect-based connector (`appconnect-connector-googleanalytics`). Use the policy file `EveryPolicy/googleanalytics.policyxml`.

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googleanalytics.msgnode`
- `applicationConnectorType="googleanalytics"` (Universal Analytics) or `applicationConnectorType="googleanalytics4"` (GA4)
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Analytics Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Google Universal Analytics Request nodes (deprecated):

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
- For Google Universal Analytics (deprecated): a suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googleuniversalanalytics`. The policy file is available at `EveryPolicy/googleuniversalanalytics.policyxml`.
- For Google Analytics 4: a suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googleanalytics`. The policy file is available at `EveryPolicy/googleanalytics.policyxml`.

## Example policy — Google Universal Analytics (deprecated)
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

## Example policy — Google Analytics 4
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googleanalytics" policyTemplate="online_v1_basic_oauth" policyType="googleanalytics4" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_OAUTH</authenticationMethod>
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
- [`loopback-connector-googleanalytics/descriptors/googleanalytics.json`](../loopback-connector-googleanalytics/descriptors/googleanalytics.json)
- [`loopback-connector-googleanalytics/descriptors/googleanalytics.yaml`](../loopback-connector-googleanalytics/descriptors/googleanalytics.yaml)
- [`loopback-connector-googleanalytics/lib/constants/gaConstants.json`](../loopback-connector-googleanalytics/lib/constants/gaConstants.json)
- [`loopback-connector-googleanalytics/lib/constants/metadata.json`](../loopback-connector-googleanalytics/lib/constants/metadata.json)
- [`appconnect-connector-googleanalytics/lib/openapi/connector.json`](../appconnect-connector-googleanalytics/lib/openapi/connector.json)
- [`EveryPolicy/googleanalytics.policyxml`](../EveryPolicy/googleanalytics.policyxml)
- [`EveryPolicy/googleuniversalanalytics.policyxml`](../EveryPolicy/googleuniversalanalytics.policyxml)
