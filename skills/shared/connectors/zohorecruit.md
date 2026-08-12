# Zoho Recruit

## Purpose
Connector-specific rules for Zoho Recruit Request nodes.

## When to use
Use this document when the requested ACE flow includes a Zoho Recruit Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Zoho Recruit Request node

## Connector type
Zoho Recruit uses the `LoopbackNative` discovery protocol with an OpenAPI spec. Operations are expressed using `summary`, `action`, and `model` attributes on the node.

## Allowed operations
The following combinations are allowed for Zoho Recruit Request nodes:

- `displayName="Create candidate"` `action="create"` `businessObject="Candidates"`
- `displayName="Retrieve candidates by advanced filters"` `action="retrievewithwhere"` `businessObject="Candidates"`
- `displayName="Retrieve candidates"` `action="retrievewithwhere"` `businessObject="Candidates"`
- `displayName="Update candidate status"` `action="update"` `businessObject="Candidates"`
- `displayName="Associate candidates with job openings"` `action="update"` `businessObject="Candidates"`
- `displayName="Create job opening"` `action="create"` `businessObject="Job openings"`
- `displayName="Retrieve job openings by advanced filters"` `action="retrievewithwhere"` `businessObject="Job openings"`
- `displayName="Retrieve job openings"` `action="retrievewithwhere"` `businessObject="Job openings"`
- `displayName="Update job opening status"` `action="update"` `businessObject="Job openings"`
- `displayName="Retrieve departments"` `action="retrievewithwhere"` `businessObject="Departments"`
- `displayName="Retrieve applications"` `action="retrievewithwhere"` `businessObject="Applications"`
- `displayName="Retrieve application by record ID"` `action="retrieve"` `businessObject="Applications"`
- `displayName="Retrieve users"` `action="retrievewithwhere"` `businessObject="Users"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Zohorecruit1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Zohorecruit1" policyTemplate="online_v1_basic_oauth" policyType="zohorecruit" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <apiUrl>https://recruit.zoho.com/recruit/v2</apiUrl>
        <tokenUrl>https://accounts.zoho.com/oauth/v2</tokenUrl>
        <isTlsEnabled>false</isTlsEnabled>
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
