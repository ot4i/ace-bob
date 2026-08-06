# IBM Sterling Inventory Visibility

## Purpose
Connector-specific rules for IBM Sterling Inventory Visibility Request nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Sterling Inventory Visibility Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Sterling Inventory Visibility Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_ibmsterlingiv.msgnode`
- `applicationConnectorType="ibmsterlingiv"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For IBM Sterling Inventory Visibility Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for IBM Sterling Inventory Visibility Request nodes:

- `displayName="Retrieve safety stocks"` `action="RETRIEVEALL"` `businessObject="SafetyStocks"`
- `displayName="Delete safety stock"` `action="DELETEALL"` `businessObject="SafetyStocks"`
- `displayName="Set safety stocks"` `action="ADDORSETSAFETYSTOCK"` `businessObject="SafetyStocks"`
- `displayName="Retrieve supplies"` `action="RETRIEVEALL"` `businessObject="Supply"`
- `displayName="Sync supply"` `action="SYNCSUPPLY"` `businessObject="Supply"`
- `displayName="Adjust supply"` `action="ADJUSTSUPPLY"` `businessObject="Supply"`
- `displayName="Retrieve demands"` `action="RETRIEVEALL"` `businessObject="Demand"`
- `displayName="Sync demand"` `action="SYNCDEMAND"` `businessObject="Demand"`
- `displayName="Adjust demand"` `action="ADJUSTDEMAND"` `businessObject="Demand"`
- `displayName="Update or create distribution group"` `action="UPSERTWITHWHERE"` `businessObject="DistributionGroup"`
- `displayName="Retrieve distribution groups"` `action="RETRIEVEALL"` `businessObject="DistributionGroup"`
- `displayName="Delete distribution group"` `action="DELETEALL"` `businessObject="DistributionGroup"`
- `displayName="Update or create ship node"` `action="UPSERTWITHWHERE"` `businessObject="ShipNode"`
- `displayName="Retrieve ship nodes"` `action="RETRIEVEALL"` `businessObject="ShipNode"`
- `displayName="Delete ship node"` `action="DELETEALL"` `businessObject="ShipNode"`
- `displayName="Get network availability"` `action="GETNETWORKAVAILABILITY"` `businessObject="NetworkAvailability"`
- `displayName="Get node availability"` `action="GETNODEAVAILABILITY"` `businessObject="NodeAvailability"`
- `displayName="Get job status"` `action="GETJOBSTATUS"` `businessObject="Job"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Ibmsterlingiv1`.
- This connector uses `applicationType="online"` and `authenticationMethod="OAUTH2_CREDENTIALS"`. The policy includes a `<tenantId>` field for the IBM Sterling tenant ID.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Ibmsterlingiv1" policyTemplate="online_v1_oauth2_credentials" policyType="ibmsterlingiv" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_CREDENTIALS</authenticationMethod>
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
