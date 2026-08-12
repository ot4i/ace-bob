# SAP Commerce Cloud

## Purpose
Connector-specific rules for SAP Commerce Cloud Request nodes.

## When to use
Use this document when the requested ACE flow includes a SAP Commerce Cloud Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- SAP Commerce Cloud Request node

## Connector type
SAP Commerce Cloud is a **dynamic (OpenAPI-based)** connector. It does not use the legacy `xmi:type` / `applicationConnectorType` attributes. The connector is implemented in [`appconnect-connector-sapcommercecloud`](../appconnect-connector-sapcommercecloud/) and exposes its operations via the OpenAPI specification at [`lib/openapi/connector.json`](../appconnect-connector-sapcommercecloud/lib/openapi/connector.json).

## Schema file requirements
For SAP Commerce Cloud Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for SAP Commerce Cloud Request nodes:

- `displayName="Retrieve base sites"` `action="retrievewithwhere"` `businessObject="Base sites"`
- `displayName="Retrieve payment card types"` `action="retrievewithwhere"` `businessObject="Payment card types"`
- `displayName="Retrieve catalogs"` `action="retrievewithwhere"` `businessObject="Catalogs"`
- `displayName="Retrieve catalog"` `action="retrieve"` `businessObject="Catalogs"`
- `displayName="Retrieve catalog version"` `action="retrieve"` `businessObject="Catalogs"`
- `displayName="Retrieve category"` `action="retrieve"` `businessObject="Catalogs"`
- `displayName="Retrieve cost centers"` `action="retrievewithwhere"` `businessObject="Cost centers"`
- `displayName="Create cost center"` `action="create"` `businessObject="Cost centers"`
- `displayName="Retrieve cost center"` `action="retrieve"` `businessObject="Cost centers"`
- `displayName="Update cost center"` `action="update"` `businessObject="Cost centers"`
- `displayName="Retrieve countries"` `action="retrievewithwhere"` `businessObject="Countries"`
- `displayName="Retrieve regions"` `action="retrievewithwhere"` `businessObject="Countries"`
- `displayName="Retrieve currencies"` `action="retrievewithwhere"` `businessObject="Currencies"`
- `displayName="Retrieve customer groups"` `action="retrievewithwhere"` `businessObject="Customer groups"`
- `displayName="Create customer group"` `action="create"` `businessObject="Customer groups"`
- `displayName="Retrieve customer group by group ID"` `action="retrieve"` `businessObject="Customer groups"`
- `displayName="Assign customer group members"` `action="update"` `businessObject="Customer groups"`
- `displayName="Delete customer group member"` `action="delete"` `businessObject="Customer groups"`
- `displayName="Retrieve customer groups by user ID"` `action="retrievewithwhere"` `businessObject="Customer groups"`
- `displayName="Retrieve languages"` `action="retrievewithwhere"` `businessObject="Languages"`
- `displayName="Retrieve order"` `action="retrieve"` `businessObject="Orders"`
- `displayName="Create order"` `action="create"` `businessObject="Orders"`
- `displayName="Retrieve products"` `action="retrievewithwhere"` `businessObject="Products"`
- `displayName="Retrieve product"` `action="retrieve"` `businessObject="Products"`
- `displayName="Retrieve product references"` `action="retrievewithwhere"` `businessObject="Products"`
- `displayName="Retrieve product reviews"` `action="retrievewithwhere"` `businessObject="Products"`
- `displayName="Retrieve product stock"` `action="retrievewithwhere"` `businessObject="Products"`
- `displayName="Retrieve product stock for store"` `action="retrieve"` `businessObject="Products"`
- `displayName="Retrieve store locations"` `action="retrievewithwhere"` `businessObject="Stores"`
- `displayName="Retrieve stores by country"` `action="retrievewithwhere"` `businessObject="Stores"`
- `displayName="Retrieve stores by country and region"` `action="retrievewithwhere"` `businessObject="Stores"`
- `displayName="Retrieve store counts"` `action="retrievewithwhere"` `businessObject="Stores"`
- `displayName="Retrieve store location by name"` `action="retrieve"` `businessObject="Stores"`
- `displayName="Retrieve customer profile"` `action="retrieve"` `businessObject="Customers"`
- `displayName="Delete customer profile"` `action="delete"` `businessObject="Customers"`
- `displayName="Update customer profile"` `action="update"` `businessObject="Customers"`
- `displayName="Retrieve customer addresses"` `action="retrievewithwhere"` `businessObject="Addresses"`
- `displayName="Create customer address"` `action="create"` `businessObject="Addresses"`
- `displayName="Retrieve customer address"` `action="retrieve"` `businessObject="Addresses"`
- `displayName="Delete customer address"` `action="delete"` `businessObject="Addresses"`
- `displayName="Update customer address"` `action="update"` `businessObject="Addresses"`
- `displayName="Retrieve user carts"` `action="retrievewithwhere"` `businessObject="Carts"`
- `displayName="Create user cart"` `action="create"` `businessObject="Carts"`
- `displayName="Retrieve user cart"` `action="retrieve"` `businessObject="Carts"`
- `displayName="Delete user cart"` `action="delete"` `businessObject="Carts"`
- `displayName="Retrieve cart pickup options"` `action="retrievewithwhere"` `businessObject="Carts"`
- `displayName="Apply cart voucher"` `action="custom"` `businessObject="Cart promotions"`
- `displayName="Retrieve cart vouchers"` `action="retrievewithwhere"` `businessObject="Cart promotions"`
- `displayName="Delete cart voucher"` `action="delete"` `businessObject="Cart promotions"`
- `displayName="Retrieve cart delivery modes"` `action="retrieve"` `businessObject="Cart delivery modes"`
- `displayName="Update cart delivery mode"` `action="update"` `businessObject="Cart delivery modes"`
- `displayName="Delete cart delivery mode"` `action="delete"` `businessObject="Cart delivery modes"`
- `displayName="Retrieve cart entries"` `action="retrievewithwhere"` `businessObject="Cart entries"`
- `displayName="Create cart entry"` `action="create"` `businessObject="Cart entries"`
- `displayName="Retrieve cart entry"` `action="retrieve"` `businessObject="Cart entries"`
- `displayName="Delete cart entry"` `action="delete"` `businessObject="Cart entries"`
- `displayName="Update cart entry"` `action="update"` `businessObject="Cart entries"`
- `displayName="Retrieve customer payment details"` `action="retrievewithwhere"` `businessObject="Payment details"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:SapCommerceCloud1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="SapCommerceCloud1" policyTemplate="online_v1_oauth2_credentials" policyType="sapcommercecloud" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>OAUTH2_CREDENTIALS</authenticationMethod>
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
