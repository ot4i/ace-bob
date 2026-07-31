# Apache Pulsar

## Purpose
Connector-specific rules for Apache Pulsar Request and Apache Pulsar Input nodes.

## When to use
Use this document when the requested ACE flow includes an Apache Pulsar Request node or Apache Pulsar Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Apache Pulsar Request node
- Apache Pulsar Input node

## Required node attributes
### Apache Pulsar Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_apachepulsar.msgnode`
- `applicationConnectorType="apachepulsar"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Apache Pulsar Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_apachepulsar.msgnode`
- `applicationConnectorType="apachepulsar"`

## Schema file requirements
For Apache Pulsar Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the validated schema prefix naming convention from the legacy guidance

## Allowed operations
The following combinations are allowed for Apache Pulsar Request nodes:

- `displayName="Publish message to topic"` `action="PUTMESSAGE"` `businessObject="publishMessageToTopic"`
- `displayName="Retrieve messages from subscription"` `action="GETMESSAGE"` `businessObject="subscribeForMessage"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:ApachePulsar1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="ApachePulsar1" policyTemplate="online_v1_basic" policyType="apachepulsar" shortDescription="" version="">
     <credentialName>ApachePulsarCredential</credentialName>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <endpointUrl/>
     <apiUrl/>
     <role/>
     <tenantId/>
     <schemaRegistryType/>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
