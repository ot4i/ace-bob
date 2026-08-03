# Google Cloud Pub/Sub

## Purpose
Connector-specific rules for Google Cloud Pub/Sub Request and Google Cloud Pub/Sub Input nodes.

## When to use
Use this document when the requested ACE flow includes a Google Cloud Pub/Sub Request node or Google Cloud Pub/Sub Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Google Cloud Pub/Sub Request node
- Google Cloud Pub/Sub Input node

## Required node attributes
### Google Cloud Pub/Sub Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_googlepubsub.msgnode`
- `applicationConnectorType="googlepubsub"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Google Cloud Pub/Sub Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_googlepubsub.msgnode`
- `applicationConnectorType="googlepubsub"`

## Schema file requirements
For Google Cloud Pub/Sub Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Google Cloud Pub/Sub Request nodes:

- `displayName="Create topic"` `action="CREATE"` `businessObject="topic"`
- `displayName="Retrieve topics"` `action="RETRIEVEALL"` `businessObject="topic"`
- `displayName="Update topic"` `action="UPDATEALL"` `businessObject="topic"`
- `displayName="Delete topic"` `action="DELETEALL"` `businessObject="topic"`
- `displayName="Create subscription"` `action="CREATE"` `businessObject="subscription"`
- `displayName="Retrieve subscriptions"` `action="RETRIEVEALL"` `businessObject="subscription"`
- `displayName="Update subscription"` `action="UPDATEALL"` `businessObject="subscription"`
- `displayName="Delete subscription"` `action="DELETEALL"` `businessObject="subscription"`
- `displayName="Create message"` `action="CREATE"` `businessObject="message"`

The following combination is allowed for Google Cloud Pub/Sub Input nodes:

- `displayName="New message"` `action="CREATED"` `businessObject="newmessage"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:googlepubsub`.
- The policy file is available at `EveryPolicy/googlepubsub.policyxml`.
- Note: this connector uses `authenticationMethod="BASIC"` with service account credentials (client email and private key). The policy requires a `<projectId/>` field and does not include a `<proxyId/>` field.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="googlepubsub" policyTemplate="online_v1_basic" policyType="googlepubsub" shortDescription="" version="">
     <credentialName/>
     <applicationVersion>v1</applicationVersion>
     <applicationType>online</applicationType>
     <authenticationMethod>BASIC</authenticationMethod>
     <projectId/>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`loopback-connector-googlepubsub/descriptors/googlepubsub.json`](../loopback-connector-googlepubsub/descriptors/googlepubsub.json)
- [`loopback-connector-googlepubsub/descriptors/googlepubsub.yaml`](../loopback-connector-googlepubsub/descriptors/googlepubsub.yaml)
- [`loopback-connector-googlepubsub/lib/models/objects.json`](../loopback-connector-googlepubsub/lib/models/objects.json)
- [`loopback-connector-googlepubsub/lib/models/topic.json`](../loopback-connector-googlepubsub/lib/models/topic.json)
- [`loopback-connector-googlepubsub/lib/models/subscription.json`](../loopback-connector-googlepubsub/lib/models/subscription.json)
- [`loopback-connector-googlepubsub/lib/models/message.json`](../loopback-connector-googlepubsub/lib/models/message.json)
- [`loopback-connector-googlepubsub/lib/models/newmessage.json`](../loopback-connector-googlepubsub/lib/models/newmessage.json)
- [`loopback-connector-googlepubsubevent/descriptors/googlepubsubevent.json`](../loopback-connector-googlepubsubevent/descriptors/googlepubsubevent.json)
- [`loopback-connector-googlepubsubevent/lib/models/newmessage.json`](../loopback-connector-googlepubsubevent/lib/models/newmessage.json)
- [`loopback-connector-googlepubsubevent/lib/models/subscription.json`](../loopback-connector-googlepubsubevent/lib/models/subscription.json)
- [`loopback-connector-googlepubsubevent/lib/models/topic.json`](../loopback-connector-googlepubsubevent/lib/models/topic.json)
- [`EveryPolicy/googlepubsub.policyxml`](../EveryPolicy/googlepubsub.policyxml)
