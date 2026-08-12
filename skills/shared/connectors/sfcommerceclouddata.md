# Salesforce Commerce Cloud Data

## Purpose
Connector-specific rules for Salesforce Commerce Cloud Data Request nodes.

## When to use
Use this document when the requested ACE flow includes a Salesforce Commerce Cloud Data Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Salesforce Commerce Cloud Data Request node

## Required node attributes
### Salesforce Commerce Cloud Data Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_sfcommerceclouddata.msgnode`
- `applicationConnectorType="sfcommerceclouddata"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Salesforce Commerce Cloud Data Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Salesforce Commerce Cloud Data Request nodes:

- `displayName="Retrieve catalogs"` `action="RETRIEVEALL"` `businessObject="catalogs"`
- `displayName="Update catalog"` `action="UPDATE"` `businessObject="catalogs"`
- `displayName="Update catalog"` `action="UPDATEALL"` `businessObject="catalogs"`
- `displayName="Retrieve categories"` `action="RETRIEVEALL"` `businessObject="categories"`
- `displayName="Delete category"` `action="DELETEALL"` `businessObject="categories"`
- `displayName="Update category"` `action="UPDATE"` `businessObject="categories"`
- `displayName="Update category"` `action="UPDATEALL"` `businessObject="categories"`
- `displayName="Create category"` `action="CREATE"` `businessObject="categories"`
- `displayName="Update or create categories"` `action="UPSERTWITHWHERE"` `businessObject="categories"`
- `displayName="Create customer"` `action="CREATE"` `businessObject="customers"`
- `displayName="Delete customer"` `action="DELETEALL"` `businessObject="customers"`
- `displayName="Retrieve customers"` `action="RETRIEVEALL"` `businessObject="customers"`
- `displayName="Update customer"` `action="UPDATE"` `businessObject="customers"`
- `displayName="Update customer"` `action="UPDATEALL"` `businessObject="customers"`
- `displayName="Update or create customers"` `action="UPSERTWITHWHERE"` `businessObject="customers"`
- `displayName="Retrieve inventory lists"` `action="RETRIEVEALL"` `businessObject="inventory_lists"`
- `displayName="Delete inventory list"` `action="DELETEALL"` `businessObject="inventory_lists"`
- `displayName="Update inventory list"` `action="UPDATE"` `businessObject="inventory_lists"`
- `displayName="Update inventory list"` `action="UPDATEALL"` `businessObject="inventory_lists"`
- `displayName="Create inventory list"` `action="CREATE"` `businessObject="inventory_lists"`
- `displayName="Update or create inventory list"` `action="UPSERTWITHWHERE"` `businessObject="inventory_lists"`
- `displayName="Retrieve product inventory records"` `action="RETRIEVEALL"` `businessObject="product_inventory_records"`
- `displayName="Delete product inventory record"` `action="DELETEALL"` `businessObject="product_inventory_records"`
- `displayName="Update product inventory record"` `action="UPDATE"` `businessObject="product_inventory_records"`
- `displayName="Update product inventory record"` `action="UPDATEALL"` `businessObject="product_inventory_records"`
- `displayName="Create product inventory record"` `action="CREATE"` `businessObject="product_inventory_records"`
- `displayName="Update or create product inventory record"` `action="UPSERTWITHWHERE"` `businessObject="product_inventory_records"`
- `displayName="Delete product"` `action="DELETEALL"` `businessObject="products"`
- `displayName="Retrieve products"` `action="RETRIEVEALL"` `businessObject="products"`
- `displayName="Update product"` `action="UPDATE"` `businessObject="products"`
- `displayName="Update product"` `action="UPDATEALL"` `businessObject="products"`
- `displayName="Create product"` `action="CREATE"` `businessObject="products"`
- `displayName="Update or create product"` `action="UPSERTWITHWHERE"` `businessObject="products"`
- `displayName="Retrieve sites"` `action="RETRIEVEALL"` `businessObject="sites"`
- `displayName="Delete campaign"` `action="DELETEALL"` `businessObject="campaigns"`
- `displayName="Retrieve campaigns"` `action="RETRIEVEALL"` `businessObject="campaigns"`
- `displayName="Update campaign"` `action="UPDATE"` `businessObject="campaigns"`
- `displayName="Update campaign"` `action="UPDATEALL"` `businessObject="campaigns"`
- `displayName="Create campaign"` `action="CREATE"` `businessObject="campaigns"`
- `displayName="Update or create campaign"` `action="UPSERTWITHWHERE"` `businessObject="campaigns"`
- `displayName="Retrieve sites coupons"` `action="RETRIEVEALL"` `businessObject="sites_coupons"`
- `displayName="Delete site coupon"` `action="DELETEALL"` `businessObject="sites_coupons"`
- `displayName="Update site coupon"` `action="UPDATE"` `businessObject="sites_coupons"`
- `displayName="Update site coupon"` `action="UPDATEALL"` `businessObject="sites_coupons"`
- `displayName="Create site coupon"` `action="CREATE"` `businessObject="sites_coupons"`
- `displayName="Update or create site coupon"` `action="UPSERTWITHWHERE"` `businessObject="sites_coupons"`
- `displayName="Delete site promotion"` `action="DELETEALL"` `businessObject="sites_promotions"`
- `displayName="Retrieve site promotions"` `action="RETRIEVEALL"` `businessObject="sites_promotions"`
- `displayName="Update site promotion"` `action="UPDATE"` `businessObject="sites_promotions"`
- `displayName="Update site promotion"` `action="UPDATEALL"` `businessObject="sites_promotions"`
- `displayName="Create site promotion"` `action="CREATE"` `businessObject="sites_promotions"`
- `displayName="Update or create site promotion"` `action="UPSERTWITHWHERE"` `businessObject="sites_promotions"`
- `displayName="Retrieve stores"` `action="RETRIEVEALL"` `businessObject="stores"`
- `displayName="Delete store"` `action="DELETEALL"` `businessObject="stores"`
- `displayName="Update store"` `action="UPDATE"` `businessObject="stores"`
- `displayName="Update store"` `action="UPDATEALL"` `businessObject="stores"`
- `displayName="Create store"` `action="CREATE"` `businessObject="stores"`
- `displayName="Update or create store"` `action="UPSERTWITHWHERE"` `businessObject="stores"`
- `displayName="Retrieve gift certificates"` `action="RETRIEVEALL"` `businessObject="gift_certificates"`
- `displayName="Create gift certificate"` `action="CREATE"` `businessObject="gift_certificates"`
- `displayName="Delete gift certificate"` `action="DELETEALL"` `businessObject="gift_certificates"`
- `displayName="Update gift certificate"` `action="UPDATE"` `businessObject="gift_certificates"`
- `displayName="Update gift certificate"` `action="UPDATEALL"` `businessObject="gift_certificates"`
- `displayName="Update or create gift certificate"` `action="UPSERTWITHWHERE"` `businessObject="gift_certificates"`
- `displayName="Retrieve site customer groups"` `action="RETRIEVEALL"` `businessObject="sites_customer_groups"`
- `displayName="Delete site customer group"` `action="DELETEALL"` `businessObject="sites_customer_groups"`
- `displayName="Update site customer group"` `action="UPDATE"` `businessObject="sites_customer_groups"`
- `displayName="Update site customer group"` `action="UPDATEALL"` `businessObject="sites_customer_groups"`
- `displayName="Create site customer group"` `action="CREATE"` `businessObject="sites_customer_groups"`
- `displayName="Update or create site customer group"` `action="UPSERTWITHWHERE"` `businessObject="sites_customer_groups"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Salesforcecommercecloud1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Salesforcecommercecloud1" policyTemplate="online_v1_oauth2_credentials" policyType="sfcommerceclouddata" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_CREDENTIALS</authenticationMethod>
        <endpointUrl/>
        <apiVersion>v23_2</apiVersion>
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
