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

- `summary="Retrieve base sites"` `action="retrievewithwhere"` `model="Base sites"`
- `summary="Retrieve payment card types"` `action="retrievewithwhere"` `model="Payment card types"`
- `summary="Retrieve catalogs"` `action="retrievewithwhere"` `model="Catalogs"`
- `summary="Retrieve catalog"` `action="retrieve"` `model="Catalogs"`
- `summary="Retrieve catalog version"` `action="retrieve"` `model="Catalogs"`
- `summary="Retrieve category"` `action="retrieve"` `model="Catalogs"`
- `summary="Retrieve cost centers"` `action="retrievewithwhere"` `model="Cost centers"`
- `summary="Create cost center"` `action="create"` `model="Cost centers"`
- `summary="Retrieve cost center"` `action="retrieve"` `model="Cost centers"`
- `summary="Update cost center"` `action="update"` `model="Cost centers"`
- `summary="Retrieve countries"` `action="retrievewithwhere"` `model="Countries"`
- `summary="Retrieve regions"` `action="retrievewithwhere"` `model="Countries"`
- `summary="Retrieve currencies"` `action="retrievewithwhere"` `model="Currencies"`
- `summary="Retrieve customer groups"` `action="retrievewithwhere"` `model="Customer groups"`
- `summary="Create customer group"` `action="create"` `model="Customer groups"`
- `summary="Retrieve customer group by group ID"` `action="retrieve"` `model="Customer groups"`
- `summary="Assign customer group members"` `action="update"` `model="Customer groups"`
- `summary="Delete customer group member"` `action="delete"` `model="Customer groups"`
- `summary="Retrieve customer groups by user ID"` `action="retrievewithwhere"` `model="Customer groups"`
- `summary="Retrieve languages"` `action="retrievewithwhere"` `model="Languages"`
- `summary="Retrieve order"` `action="retrieve"` `model="Orders"`
- `summary="Create order"` `action="create"` `model="Orders"`
- `summary="Retrieve products"` `action="retrievewithwhere"` `model="Products"`
- `summary="Retrieve product"` `action="retrieve"` `model="Products"`
- `summary="Retrieve product references"` `action="retrievewithwhere"` `model="Products"`
- `summary="Retrieve product reviews"` `action="retrievewithwhere"` `model="Products"`
- `summary="Retrieve product stock"` `action="retrievewithwhere"` `model="Products"`
- `summary="Retrieve product stock for store"` `action="retrieve"` `model="Products"`
- `summary="Retrieve store locations"` `action="retrievewithwhere"` `model="Stores"`
- `summary="Retrieve stores by country"` `action="retrievewithwhere"` `model="Stores"`
- `summary="Retrieve stores by country and region"` `action="retrievewithwhere"` `model="Stores"`
- `summary="Retrieve store counts"` `action="retrievewithwhere"` `model="Stores"`
- `summary="Retrieve store location by name"` `action="retrieve"` `model="Stores"`
- `summary="Retrieve customer profile"` `action="retrieve"` `model="Customers"`
- `summary="Delete customer profile"` `action="delete"` `model="Customers"`
- `summary="Update customer profile"` `action="update"` `model="Customers"`
- `summary="Retrieve customer addresses"` `action="retrievewithwhere"` `model="Addresses"`
- `summary="Create customer address"` `action="create"` `model="Addresses"`
- `summary="Retrieve customer address"` `action="retrieve"` `model="Addresses"`
- `summary="Delete customer address"` `action="delete"` `model="Addresses"`
- `summary="Update customer address"` `action="update"` `model="Addresses"`
- `summary="Retrieve user carts"` `action="retrievewithwhere"` `model="Carts"`
- `summary="Create user cart"` `action="create"` `model="Carts"`
- `summary="Retrieve user cart"` `action="retrieve"` `model="Carts"`
- `summary="Delete user cart"` `action="delete"` `model="Carts"`
- `summary="Retrieve cart pickup options"` `action="retrievewithwhere"` `model="Carts"`
- `summary="Apply cart voucher"` `action="custom"` `model="Cart promotions"`
- `summary="Retrieve cart vouchers"` `action="retrievewithwhere"` `model="Cart promotions"`
- `summary="Delete cart voucher"` `action="delete"` `model="Cart promotions"`
- `summary="Retrieve cart delivery modes"` `action="retrieve"` `model="Cart delivery modes"`
- `summary="Update cart delivery mode"` `action="update"` `model="Cart delivery modes"`
- `summary="Delete cart delivery mode"` `action="delete"` `model="Cart delivery modes"`
- `summary="Retrieve cart entries"` `action="retrievewithwhere"` `model="Cart entries"`
- `summary="Create cart entry"` `action="create"` `model="Cart entries"`
- `summary="Retrieve cart entry"` `action="retrieve"` `model="Cart entries"`
- `summary="Delete cart entry"` `action="delete"` `model="Cart entries"`
- `summary="Update cart entry"` `action="update"` `model="Cart entries"`
- `summary="Retrieve customer payment details"` `action="retrievewithwhere"` `model="Payment details"`

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
