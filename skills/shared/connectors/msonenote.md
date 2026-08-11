# Microsoft OneNote

## Purpose
Connector-specific rules for Microsoft OneNote Request nodes.

## When to use
Use this document when the requested ACE flow includes a Microsoft OneNote Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Microsoft OneNote Request node

## Required node attributes
### Microsoft OneNote Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_msonenote.msgnode`
- `applicationConnectorType="msonenote"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For Microsoft OneNote Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Microsoft OneNote Request nodes:

- `displayName="Create notebook"` `action="CREATE"` `businessObject="Notebook"`
- `displayName="Retrieve notebooks"` `action="RETRIEVEALL"` `businessObject="Notebook"`
- `displayName="Retrieve notebook"` `action="RETRIEVE"` `businessObject="Notebook"`
- `displayName="Create section"` `action="CREATE"` `businessObject="Section"`
- `displayName="Retrieve sections"` `action="RETRIEVEALL"` `businessObject="Section"`
- `displayName="Retrieve section"` `action="RETRIEVE"` `businessObject="Section"`
- `displayName="Create section group"` `action="CREATE"` `businessObject="SectionGroup"`
- `displayName="Retrieve section groups"` `action="RETRIEVEALL"` `businessObject="SectionGroup"`
- `displayName="Retrieve section group"` `action="RETRIEVE"` `businessObject="SectionGroup"`
- `displayName="Create page"` `action="CREATE"` `businessObject="Page"`
- `displayName="Retrieve pages"` `action="RETRIEVEALL"` `businessObject="Page"`
- `displayName="Retrieve page"` `action="RETRIEVE"` `businessObject="Page"`
- `displayName="Delete page"` `action="DELETEALL"` `businessObject="Page"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:MSOneNote1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="MSOneNote1" policyTemplate="online_v1_basic_oauth" policyType="msonenote" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
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
