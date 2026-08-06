# IBM Maximo

## Purpose
Connector-specific rules for IBM Maximo Request and IBM Maximo Input nodes.

## When to use
Use this document when the requested ACE flow includes an IBM Maximo Request node or IBM Maximo Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- IBM Maximo Request node
- IBM Maximo Input node

## Required node attributes
### IBM Maximo Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_maximo.msgnode`
- `applicationConnectorType="maximo"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### IBM Maximo Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_maximo.msgnode`
- `applicationConnectorType="maximo"`

## Schema file requirements
For IBM Maximo Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
IBM Maximo uses dynamic discovery — business objects are discovered at runtime from the Maximo API and are not statically defined. The following operations are supported across all discovered business objects for IBM Maximo Request nodes:

- `action="CREATE"` — create a record
- `action="RETRIEVEALL"` — retrieve records
- `action="UPDATEALL"` — update a record
- `action="DELETEALL"` — delete a record
- `action="UPSERTWITHWHERE"` — update or create a record
- `action="REPLACEORCREATE_RM"` — replace or create a record using resource management
- `action="REPLACEPATCH"` — replace or patch a record by ID
- `action="DOWNLOADCSV"` — download records as CSV

The following combinations are allowed for IBM Maximo Input nodes:

- `displayName="New record"` `action="CREATED"` `businessObject="<objectName>"`
- `displayName="Updated record"` `action="UPDATED"` `businessObject="<objectName>"`
- `displayName="Deleted record"` `action="DELETED"` `businessObject="<objectName>"`

The IBM Maximo Input node is provided by the webhooks connector. Objects that support events include: `MXAPIPERUSER`, `MXAPIPERSONGROUP`, `MXAPIASSET`, `MXAPISERADDRESS`, `MXAPISR`, `MXAPICRAFT`, `MXAPICONTRACT`, `MXAPIVENDOR`, `MXAPIWO`, `MXAPIPO`, and `MXAPILABOR`.

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Maximo1`.
- This connector uses `applicationType="onprem"` and `authenticationMethod="BASIC"`. The policy includes an `<endpointUrl>` field for the Maximo on-premises instance URL.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Maximo1" policyTemplate="onprem_v1_basic" policyType="maximo" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>onprem</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
