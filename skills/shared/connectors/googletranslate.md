# Google Translate

## Purpose
Connector-specific rules for Google Translate Request nodes.

## When to use
Use this document when the requested ACE flow includes a Google Translate Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Translate Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googletranslate.msgnode`
- `applicationConnectorType="googletranslate"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Google Translate Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Translate Request nodes:

- `displayName="Retrieve locations"` `action="RETRIEVEWITHWHERE"` `businessObject="Locations"`
- `displayName="Translate text"` `action="CUSTOM"` `businessObject="Translate"`
- `displayName="Detect language"` `action="CUSTOM"` `businessObject="Translate"`
- `displayName="Translate document"` `action="CUSTOM"` `businessObject="Translate"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googletranslate`.
- The policy file is available at `EveryPolicy/googletranslate.policyxml`.
- Note: this connector uses `authenticationMethod="BASIC_OAUTH"` and includes an `<apiUrl/>` field for the Google Translate service endpoint URL (for example, `https://translate.googleapis.com/v3/projects/<projectID>`). It also supports `OAUTH2_WEB` authentication.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googletranslate" policyTemplate="online_v1_basic_oauth" policyType="googletranslate" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC_OAUTH</authenticationMethod>
     <apiUrl/>
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
- [`loopback-connector-googletranslate/descriptors/googletranslate.json`](../loopback-connector-googletranslate/descriptors/googletranslate.json)
- [`loopback-connector-googletranslate/descriptors/googletranslate.yaml`](../loopback-connector-googletranslate/descriptors/googletranslate.yaml)
- [`loopback-connector-googletranslate/lib/openapi/connector.json`](../loopback-connector-googletranslate/lib/openapi/connector.json)
- [`appconnect-connector-googletranslate/lib/openapi/connector.json`](../appconnect-connector-googletranslate/lib/openapi/connector.json)
- [`EveryPolicy/googletranslate.policyxml`](../EveryPolicy/googletranslate.policyxml)
