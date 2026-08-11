# Azure Service Bus

## Purpose
Connector-specific rules for Azure Service Bus Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes an Azure Service Bus Request node or an Azure Service Bus Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Azure Service Bus Request node
- Azure Service Bus Input node

## Required node attributes
### Azure Service Bus Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_azureservicebus.msgnode`
- `applicationConnectorType="azureservicebus"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Azure Service Bus Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_azureservicebus.msgnode`
- `applicationConnectorType="azureservicebus"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Azure Service Bus Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

For Azure Service Bus Input nodes:
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Azure Service Bus Request nodes:

- `displayName="Create queue"` `action="CREATE"` `businessObject="Queue"`
- `displayName="Update queue"` `action="UPDATEALL"` `businessObject="Queue"`
- `displayName="Retrieve queues"` `action="RETRIEVEALL"` `businessObject="Queue"`
- `displayName="Retrieve queue"` `action="RETRIEVE"` `businessObject="Queue"`
- `displayName="Delete queue"` `action="DELETEALL"` `businessObject="Queue"`
- `displayName="Create topic"` `action="CREATE"` `businessObject="Topic"`
- `displayName="Update topic"` `action="UPDATEALL"` `businessObject="Topic"`
- `displayName="Retrieve topics"` `action="RETRIEVEALL"` `businessObject="Topic"`
- `displayName="Retrieve topic"` `action="RETRIEVE"` `businessObject="Topic"`
- `displayName="Delete topic"` `action="DELETEALL"` `businessObject="Topic"`
- `displayName="Create subscription"` `action="CREATE"` `businessObject="Subscription"`
- `displayName="Update subscription"` `action="UPDATEALL"` `businessObject="Subscription"`
- `displayName="Retrieve subscriptions"` `action="RETRIEVEALL"` `businessObject="Subscription"`
- `displayName="Retrieve subscription"` `action="RETRIEVE"` `businessObject="Subscription"`
- `displayName="Delete subscription"` `action="DELETEALL"` `businessObject="Subscription"`
- `displayName="Send message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Receive messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Dead-letter message"` `action="CUSTOM"` `businessObject="Message"`

The following combinations are allowed for Azure Service Bus Input nodes:

- `displayName="New message"` `action="CREATED"` `businessObject="Message"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AzureServiceBus1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="AzureServiceBus1" policyTemplate="online_v1_basic" policyType="azureservicebus" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
        <tenantId/>
        <endpointUrl/>
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
