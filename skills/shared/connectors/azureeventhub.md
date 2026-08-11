# Azure Event Hubs

## Purpose
Connector-specific rules for Azure Event Hubs Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes an Azure Event Hubs Request node or an Azure Event Hubs Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Azure Event Hubs Request node
- Azure Event Hubs Input node

## Required node attributes
### Azure Event Hubs Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_azureeventhub.msgnode`
- `applicationConnectorType="azureeventhub"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Azure Event Hubs Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_azureeventhub.msgnode`
- `applicationConnectorType="azureeventhub"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Azure Event Hubs Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

For Azure Event Hubs Input nodes:
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Azure Event Hubs Request nodes:

- `displayName="Create event hub"` `action="CREATE"` `businessObject="EventHub"`
- `displayName="Update event hub"` `action="UPDATEALL"` `businessObject="EventHub"`
- `displayName="Retrieve event hubs"` `action="RETRIEVEALL"` `businessObject="EventHub"`
- `displayName="Retrieve event hub"` `action="RETRIEVE"` `businessObject="EventHub"`
- `displayName="Delete event hub"` `action="DELETEALL"` `businessObject="EventHub"`
- `displayName="Retrieve consumer groups"` `action="RETRIEVEALL"` `businessObject="ConsumerGroup"`
- `displayName="Retrieve consumer group"` `action="RETRIEVE"` `businessObject="ConsumerGroup"`
- `displayName="Retrieve partitions"` `action="RETRIEVEALL"` `businessObject="Partition"`
- `displayName="Retrieve partition"` `action="RETRIEVE"` `businessObject="Partition"`
- `displayName="Create message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Retrieve message"` `action="RETRIEVE"` `businessObject="Message"`

The following combinations are allowed for Azure Event Hubs Input nodes:

- `displayName="New message"` `action="CREATED"` `businessObject="Message"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:AzureEventHub1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="AzureEventHub1" policyTemplate="online_v1_basic_oauth" policyType="azureeventhub" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <tenantId/>
        <roleArn/>
        <role/>
        <region/>
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
