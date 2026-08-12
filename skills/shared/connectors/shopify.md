# Shopify

## Purpose
Connector-specific rules for Shopify Request nodes.

## When to use
Use this document when the requested ACE flow includes a Shopify Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Shopify Request node

## Required node attributes
### Shopify Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_shopify.msgnode`
- `applicationConnectorType="shopify"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Shopify Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Shopify Request nodes:

- `displayName="Create customer"` `action="CREATE"` `businessObject="Customer"`
- `displayName="Retrieve customers"` `action="RETRIEVEALL"` `businessObject="Customer"`
- `displayName="Retrieve customer"` `action="RETRIEVE"` `businessObject="Customer"`
- `displayName="Update customer"` `action="UPDATEALL"` `businessObject="Customer"`
- `displayName="Update or create customer"` `action="UPSERTWITHWHERE"` `businessObject="Customer"`
- `displayName="Create customer address"` `action="CREATE"` `businessObject="CustomerAddress"`
- `displayName="Retrieve customer addresses"` `action="RETRIEVEALL"` `businessObject="CustomerAddress"`
- `displayName="Retrieve customer address"` `action="RETRIEVE"` `businessObject="CustomerAddress"`
- `displayName="Create order"` `action="CREATE"` `businessObject="Order"`
- `displayName="Retrieve orders"` `action="RETRIEVEALL"` `businessObject="Order"`
- `displayName="Retrieve order"` `action="RETRIEVE"` `businessObject="Order"`
- `displayName="Update order"` `action="UPDATEALL"` `businessObject="Order"`
- `displayName="Delete order"` `action="DELETEALL"` `businessObject="Order"`
- `displayName="Update or create order"` `action="UPSERTWITHWHERE"` `businessObject="Order"`
- `displayName="Create product"` `action="CREATE"` `businessObject="Product"`
- `displayName="Retrieve products"` `action="RETRIEVEALL"` `businessObject="Product"`
- `displayName="Retrieve product"` `action="RETRIEVE"` `businessObject="Product"`
- `displayName="Update product"` `action="UPDATEALL"` `businessObject="Product"`
- `displayName="Update or create product"` `action="UPSERTWITHWHERE"` `businessObject="Product"`
- `displayName="Retrieve inventory items"` `action="RETRIEVEALL"` `businessObject="InventoryItem"`
- `displayName="Retrieve inventory item"` `action="RETRIEVE"` `businessObject="InventoryItem"`
- `displayName="Update inventory item"` `action="UPDATEALL"` `businessObject="InventoryItem"`
- `displayName="Create inventory level"` `action="CREATE"` `businessObject="InventoryLevel"`
- `displayName="Retrieve inventory levels"` `action="RETRIEVEALL"` `businessObject="InventoryLevel"`
- `displayName="Retrieve inventory level"` `action="RETRIEVE"` `businessObject="InventoryLevel"`
- `displayName="Retrieve locations"` `action="RETRIEVEALL"` `businessObject="Location"`
- `displayName="Retrieve location"` `action="RETRIEVE"` `businessObject="Location"`
- `displayName="Retrieve transactions"` `action="RETRIEVEALL"` `businessObject="Transaction"`
- `displayName="Retrieve transaction"` `action="RETRIEVE"` `businessObject="Transaction"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Shopify1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Shopify1" policyTemplate="online_v1_basic_api_key" policyType="shopify" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <accountName/>
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
