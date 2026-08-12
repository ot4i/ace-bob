# Oracle E-Business Suite

## Purpose
Connector-specific rules for Oracle E-Business Suite Request nodes.

## When to use
Use this document when the requested ACE flow includes an Oracle E-Business Suite Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Oracle E-Business Suite Request node

## Required node attributes
### Oracle E-Business Suite Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_oracleebs.msgnode`
- `applicationConnectorType="oracleebs"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Oracle E-Business Suite Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Oracle E-Business Suite Request nodes:

- `displayName="Create order"` `action="CREATE_ORDER"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Update order"` `action="UPDATE_ORDER"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Delete order"` `action="DELETE_ORDER"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Create order with header"` `action="CREATE_HEADER"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Update order with header"` `action="UPDATE_HEADER"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Create order line items"` `action="CREATE_LINE_ITEM"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Update order line items"` `action="UPDATE_LINE_ITEM"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Delete order line item"` `action="DELETE_LINE_ITEM"` `businessObject="OE_INBOUND_INT_Service___PROCESS_ORDER"`
- `displayName="Get order"` `action="GET_ORDER"` `businessObject="OE_INBOUND_INT_Service___GET_ORDER"`
- `displayName="Create delivery line"` `action="AUTOCREATE_DELIVERIES"` `businessObject="WSH_DELIVERY_DETAILS_PUB_Service___AUTOCREATE_DELIVERIES"`
- `displayName="Update delivery line"` `action="UPDATE_SHIPPING_ATTRIBUTES"` `businessObject="WSH_DELIVERY_DETAILS_PUB_Service___UPDATE_SHIPPING_ATTRIBUTES"`
- `displayName="Create pick release"` `action="PICK_RELEASE"` `businessObject="WSH_DELIVERIES_PUB_Service___DELIVERY_ACTION"`
- `displayName="Create ship confirm"` `action="SHIP_CONFIRMATION"` `businessObject="WSH_DELIVERIES_PUB_Service___DELIVERY_ACTION"`
- `displayName="Create customer"` `action="CREATE_CUST_ACCOUNT__1"` `businessObject="HZ_CUST_ACCOUNT_V2PUB_Service___CREATE_CUST_ACCOUNT__1"`
- `displayName="Update customer"` `action="UPDATE_CUST_ACCOUNT"` `businessObject="HZ_CUST_ACCOUNT_V2PUB_Service___UPDATE_CUST_ACCOUNT"`
- `displayName="Create location"` `action="CREATE_LOCATION"` `businessObject="HZ_LOCATION_V2PUB_Service___CREATE_LOCATION"`
- `displayName="Update location"` `action="UPDATE_LOCATION"` `businessObject="HZ_LOCATION_V2PUB_Service___UPDATE_LOCATION"`
- `displayName="Create party site"` `action="CREATE_PARTY_SITE"` `businessObject="HZ_PARTY_SITE_V2PUB_Service___CREATE_PARTY_SITE"`
- `displayName="Update party site"` `action="UPDATE_PARTY_SITE"` `businessObject="HZ_PARTY_SITE_V2PUB_Service___UPDATE_PARTY_SITE"`
- `displayName="Create customer site"` `action="CREATE_CUST_ACCT_SITE"` `businessObject="HZ_CUST_ACCOUNT_SITE_V2PUB_Service___CREATE_CUST_ACCT_SITE"`
- `displayName="Create customer site address"` `action="CREATE_CUST_SITE_USE"` `businessObject="HZ_CUST_ACCOUNT_SITE_V2PUB_Service___CREATE_CUST_SITE_USE"`
- `displayName="Create organization"` `action="CREATE_ORGANIZATION"` `businessObject="HZ_PARTY_V2PUB_Service___CREATE_ORGANIZATION"`
- `displayName="Update party contact"` `action="UPDATE_ORG_CONTACT"` `businessObject="HZ_PARTY_CONTACT_V2PUB_Service___UPDATE_ORG_CONTACT"`
- `displayName="Create cash receipt"` `action="CREATE_CASH"` `businessObject="AR_RECEIPT_API_PUB_Service___CREATE_CASH"`
- `displayName="Apply receipt"` `action="APPLY"` `businessObject="AR_RECEIPT_API_PUB_Service___APPLY"`
- `displayName="Unapply receipt"` `action="UNAPPLY"` `businessObject="AR_RECEIPT_API_PUB_Service___UNAPPLY"`
- `displayName="Create vendor"` `action="CREATE_VENDOR"` `businessObject="AP_VENDOR_PUB_PKG_Service___CREATE_VENDOR"`
- `displayName="Update vendor"` `action="UPDATE_VENDOR"` `businessObject="AP_VENDOR_PUB_PKG_Service___UPDATE_VENDOR"`
- `displayName="Create single invoice"` `action="CREATE_SINGLE_INVOICE"` `businessObject="AR_INVOICE_API_PUB_Service___CREATE_SINGLE_INVOICE"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Oracleebs1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Oracleebs1" policyTemplate="online_v1_basic" policyType="oracleebs" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <instanceId/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
