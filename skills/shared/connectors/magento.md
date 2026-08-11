# Magento

## Purpose
Connector-specific rules for Magento Request and Magento Input nodes.

## When to use
Use this document when the requested ACE flow includes a Magento Request node or Magento Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Magento Request node
- Magento Input node

## Required node attributes
### Magento Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_magento.msgnode`
- `applicationConnectorType="magento"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Magento Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_magento.msgnode`
- `applicationConnectorType="magento"`

## Schema file requirements
For Magento Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Magento Request nodes:

- `displayName="Create customer"` `action="CREATE"` `businessObject="Customer"`
- `displayName="Retrieve customer"` `action="RETRIEVE"` `businessObject="Customer"`
- `displayName="Retrieve customers"` `action="RETRIEVEALL"` `businessObject="Customer"`
- `displayName="Update customer"` `action="UPDATEALL"` `businessObject="Customer"`
- `displayName="Delete customer"` `action="DELETEALL"` `businessObject="Customer"`
- `displayName="Create product"` `action="CREATE"` `businessObject="Product"`
- `displayName="Retrieve product"` `action="RETRIEVE"` `businessObject="Product"`
- `displayName="Retrieve products"` `action="RETRIEVEALL"` `businessObject="Product"`
- `displayName="Update product"` `action="UPDATEALL"` `businessObject="Product"`
- `displayName="Delete product"` `action="DELETEALL"` `businessObject="Product"`
- `displayName="Update or create product"` `action="UPSERTWITHWHERE"` `businessObject="Product"`
- `displayName="Create sales credit memo"` `action="CREATE"` `businessObject="SalesCreditMemo"`
- `displayName="Retrieve sales credit memo"` `action="RETRIEVE"` `businessObject="SalesCreditMemo"`
- `displayName="Retrieve sales credit memos"` `action="RETRIEVEALL"` `businessObject="SalesCreditMemo"`
- `displayName="Create sales invoice"` `action="CREATE"` `businessObject="SalesInvoice"`
- `displayName="Retrieve sales invoice"` `action="RETRIEVE"` `businessObject="SalesInvoice"`
- `displayName="Retrieve sales invoices"` `action="RETRIEVEALL"` `businessObject="SalesInvoice"`
- `displayName="Retrieve sales order"` `action="RETRIEVE"` `businessObject="SalesOrder"`
- `displayName="Retrieve sales orders"` `action="RETRIEVEALL"` `businessObject="SalesOrder"`
- `displayName="Update sales order"` `action="UPDATEALL"` `businessObject="SalesOrder"`
- `displayName="Retrieve sales shipment"` `action="RETRIEVE"` `businessObject="SalesShipment"`
- `displayName="Retrieve sales shipments"` `action="RETRIEVEALL"` `businessObject="SalesShipment"`
- `displayName="Create category"` `action="CREATE"` `businessObject="Category"`
- `displayName="Retrieve category"` `action="RETRIEVE"` `businessObject="Category"`
- `displayName="Retrieve categories"` `action="RETRIEVEALL"` `businessObject="Category"`
- `displayName="Update category"` `action="UPDATEALL"` `businessObject="Category"`
- `displayName="Delete category"` `action="DELETEALL"` `businessObject="Category"`
- `displayName="Create customer group"` `action="CREATE"` `businessObject="CustomerGroup"`
- `displayName="Retrieve customer group"` `action="RETRIEVE"` `businessObject="CustomerGroup"`
- `displayName="Retrieve customer groups"` `action="RETRIEVEALL"` `businessObject="CustomerGroup"`
- `displayName="Update customer group"` `action="UPDATEALL"` `businessObject="CustomerGroup"`
- `displayName="Delete customer group"` `action="DELETEALL"` `businessObject="CustomerGroup"`
- `displayName="Create cart"` `action="CREATE"` `businessObject="Cart"`
- `displayName="Retrieve cart"` `action="RETRIEVE"` `businessObject="Cart"`
- `displayName="Retrieve carts"` `action="RETRIEVEALL"` `businessObject="Cart"`
- `displayName="Update cart"` `action="UPDATEALL"` `businessObject="Cart"`
- `displayName="Create sales rule"` `action="CREATE"` `businessObject="SalesRule"`
- `displayName="Retrieve sales rule"` `action="RETRIEVE"` `businessObject="SalesRule"`
- `displayName="Retrieve sales rules"` `action="RETRIEVEALL"` `businessObject="SalesRule"`
- `displayName="Update sales rule"` `action="UPDATEALL"` `businessObject="SalesRule"`
- `displayName="Delete sales rule"` `action="DELETEALL"` `businessObject="SalesRule"`
- `displayName="Create sales rule coupon"` `action="CREATE"` `businessObject="SalesRuleCoupon"`
- `displayName="Retrieve sales rule coupon"` `action="RETRIEVE"` `businessObject="SalesRuleCoupon"`
- `displayName="Retrieve sales rule coupons"` `action="RETRIEVEALL"` `businessObject="SalesRuleCoupon"`
- `displayName="Update sales rule coupon"` `action="UPDATEALL"` `businessObject="SalesRuleCoupon"`
- `displayName="Delete sales rule coupon"` `action="DELETEALL"` `businessObject="SalesRuleCoupon"`
- `displayName="Retrieve sales transaction"` `action="RETRIEVE"` `businessObject="SalesTransaction"`
- `displayName="Retrieve sales transactions"` `action="RETRIEVEALL"` `businessObject="SalesTransaction"`

The following combinations are allowed for Magento Input nodes:

- `displayName="New customer"` `action="CREATED"` `businessObject="Customer"`
- `displayName="Updated customer"` `action="UPDATED"` `businessObject="Customer"`
- `displayName="Deleted customer"` `action="DELETED"` `businessObject="Customer"`
- `displayName="New product"` `action="CREATED"` `businessObject="Product"`
- `displayName="Updated product"` `action="UPDATED"` `businessObject="Product"`
- `displayName="Deleted product"` `action="DELETED"` `businessObject="Product"`
- `displayName="New sales credit memo"` `action="CREATED"` `businessObject="SalesCreditMemo"`
- `displayName="Updated sales credit memo"` `action="UPDATED"` `businessObject="SalesCreditMemo"`
- `displayName="Deleted sales credit memo"` `action="DELETED"` `businessObject="SalesCreditMemo"`
- `displayName="New sales invoice"` `action="CREATED"` `businessObject="SalesInvoice"`
- `displayName="Updated sales invoice"` `action="UPDATED"` `businessObject="SalesInvoice"`
- `displayName="Deleted sales invoice"` `action="DELETED"` `businessObject="SalesInvoice"`
- `displayName="New sales order"` `action="CREATED"` `businessObject="SalesOrder"`
- `displayName="Updated sales order"` `action="UPDATED"` `businessObject="SalesOrder"`
- `displayName="Deleted sales order"` `action="DELETED"` `businessObject="SalesOrder"`
- `displayName="New sales shipment"` `action="CREATED"` `businessObject="SalesShipment"`
- `displayName="Updated sales shipment"` `action="UPDATED"` `businessObject="SalesShipment"`
- `displayName="Deleted sales shipment"` `action="DELETED"` `businessObject="SalesShipment"`
- `displayName="New cart"` `action="CREATED"` `businessObject="Cart"`
- `displayName="Updated cart"` `action="UPDATED"` `businessObject="Cart"`
- `displayName="Deleted cart"` `action="DELETED"` `businessObject="Cart"`
- `displayName="New category"` `action="CREATED"` `businessObject="Category"`
- `displayName="Updated category"` `action="UPDATED"` `businessObject="Category"`
- `displayName="Deleted category"` `action="DELETED"` `businessObject="Category"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Magento1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Magento1" policyTemplate="online_v1_basic" policyType="magento" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
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
