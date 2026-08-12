# Square

## Purpose
Connector-specific rules for Square Request nodes.

## When to use
Use this document when the requested ACE flow includes a Square Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Square Request node

## Required node attributes
### Square Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_square.msgnode`
- `applicationConnectorType="square"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Square Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Square Request nodes:

- `displayName="Create customer"` `action="CREATE"` `businessObject="Customer"`
- `displayName="Retrieve customers"` `action="RETRIEVEALL"` `businessObject="Customer"`
- `displayName="Retrieve customer"` `action="RETRIEVE"` `businessObject="Customer"`
- `displayName="Update customer"` `action="UPDATEALL"` `businessObject="Customer"`
- `displayName="Delete customer"` `action="DELETEALL"` `businessObject="Customer"`
- `displayName="Update or create customer"` `action="UPSERTWITHWHERE"` `businessObject="Customer"`
- `displayName="Retrieve payments"` `action="RETRIEVEALL"` `businessObject="Payment"`
- `displayName="Retrieve payment"` `action="RETRIEVE"` `businessObject="Payment"`
- `displayName="Update payment"` `action="UPDATEALL"` `businessObject="Payment"`
- `displayName="Update or create payment"` `action="UPSERTWITHWHERE"` `businessObject="Payment"`
- `displayName="Create order"` `action="CREATE"` `businessObject="Order"`
- `displayName="Retrieve orders"` `action="RETRIEVEALL"` `businessObject="Order"`
- `displayName="Retrieve order"` `action="RETRIEVE"` `businessObject="Order"`
- `displayName="Update order"` `action="UPDATEALL"` `businessObject="Order"`
- `displayName="Update or create order"` `action="UPSERTWITHWHERE"` `businessObject="Order"`
- `displayName="Search orders"` `action="SEARCHORDER"` `businessObject="Order"`
- `displayName="Create invoice"` `action="CREATE"` `businessObject="Invoice"`
- `displayName="Retrieve invoices"` `action="RETRIEVEALL"` `businessObject="Invoice"`
- `displayName="Retrieve invoice"` `action="RETRIEVE"` `businessObject="Invoice"`
- `displayName="Update invoice"` `action="UPDATEALL"` `businessObject="Invoice"`
- `displayName="Delete invoice"` `action="DELETEALL"` `businessObject="Invoice"`
- `displayName="Update or create invoice"` `action="UPSERTWITHWHERE"` `businessObject="Invoice"`
- `displayName="Create refund"` `action="CREATE"` `businessObject="Refund"`
- `displayName="Retrieve refunds"` `action="RETRIEVEALL"` `businessObject="Refund"`
- `displayName="Create inventory"` `action="CREATE"` `businessObject="Inventory"`
- `displayName="Retrieve inventory"` `action="RETRIEVEALL"` `businessObject="Inventory"`
- `displayName="Create batch change inventory"` `action="BATCHCHANGEINVENTORY"` `businessObject="Inventory"`
- `displayName="Retrieve batch change inventory"` `action="RETRIEVEBATCHCHANGE"` `businessObject="Inventory"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Square1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Square1" policyTemplate="online_v1_basic_api_key" policyType="square" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_API_KEY</authenticationMethod>
        <endpointUrl>connect.squareup.com</endpointUrl>
        <redirectUri/>
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
