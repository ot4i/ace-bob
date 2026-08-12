# SurveyMonkey

## Purpose
Connector-specific rules for SurveyMonkey Request and SurveyMonkey Input nodes.

## When to use
Use this document when the requested ACE flow includes a SurveyMonkey Request node or SurveyMonkey Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- SurveyMonkey Request node
- SurveyMonkey Input node

## Required node attributes
### SurveyMonkey Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_surveymonkey.msgnode`
- `applicationConnectorType="surveymonkey"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### SurveyMonkey Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_surveymonkey.msgnode`
- `applicationConnectorType="surveymonkey"`

## Schema file requirements
For SurveyMonkey Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for SurveyMonkey Request nodes:

- `displayName="Create collector"` `action="CREATE"` `businessObject="Collector"`
- `displayName="Retrieve collectors"` `action="RETRIEVEALL"` `businessObject="Collector"`
- `displayName="Retrieve collector"` `action="RETRIEVE"` `businessObject="Collector"`
- `displayName="Update collector"` `action="UPDATEALL"` `businessObject="Collector"`
- `displayName="Delete collector"` `action="DELETEALL"` `businessObject="Collector"`
- `displayName="Create message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Retrieve message"` `action="RETRIEVE"` `businessObject="Message"`
- `displayName="Update message"` `action="UPDATEALL"` `businessObject="Message"`
- `displayName="Delete message"` `action="DELETEALL"` `businessObject="Message"`
- `displayName="Send message"` `action="SENDMESSAGE"` `businessObject="Message"`
- `displayName="Create recipient"` `action="CREATE"` `businessObject="Recipient"`
- `displayName="Retrieve recipients"` `action="RETRIEVEALL"` `businessObject="Recipient"`
- `displayName="Retrieve recipient"` `action="RETRIEVE"` `businessObject="Recipient"`
- `displayName="Delete recipient"` `action="DELETEALL"` `businessObject="Recipient"`
- `displayName="Retrieve survey responses"` `action="RETRIEVEALL"` `businessObject="SurveyResponse"`
- `displayName="Retrieve survey response"` `action="RETRIEVE"` `businessObject="SurveyResponse"`
- `displayName="Retrieve users"` `action="RETRIEVEALL"` `businessObject="User"`
- `displayName="Retrieve groups"` `action="RETRIEVEALL"` `businessObject="Group"`
- `displayName="Retrieve group"` `action="RETRIEVE"` `businessObject="Group"`
- `displayName="Retrieve questions"` `action="RETRIEVEALL"` `businessObject="Question"`
- `displayName="Retrieve question"` `action="RETRIEVE"` `businessObject="Question"`
- `displayName="Retrieve pages"` `action="RETRIEVEALL"` `businessObject="Page"`
- `displayName="Retrieve page"` `action="RETRIEVE"` `businessObject="Page"`
- `displayName="Retrieve surveys"` `action="RETRIEVEALL"` `businessObject="Survey"`
- `displayName="Retrieve survey"` `action="RETRIEVE"` `businessObject="Survey"`
- `displayName="Create contact list"` `action="CREATE"` `businessObject="ContactList"`
- `displayName="Retrieve contact lists"` `action="RETRIEVEALL"` `businessObject="ContactList"`
- `displayName="Retrieve contact list"` `action="RETRIEVE"` `businessObject="ContactList"`
- `displayName="Update contact list"` `action="UPDATEALL"` `businessObject="ContactList"`
- `displayName="Delete contact list"` `action="DELETEALL"` `businessObject="ContactList"`
- `displayName="Copy contact list"` `action="COPYCONTACTLIST"` `businessObject="ContactList"`
- `displayName="Merge contact list"` `action="MERGECONTACTLIST"` `businessObject="ContactList"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contact"`
- `displayName="Retrieve contact"` `action="RETRIEVE"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contact"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contact"`

The following combinations are allowed for SurveyMonkey Input nodes:

- `displayName="New response"` `action="CREATED"` `businessObject="Response"`
- `displayName="Updated response"` `action="UPDATED"` `businessObject="Response"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:SurveyMonkey1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="SurveyMonkey1" policyTemplate="online_v1_basic_oauth" policyType="surveymonkey" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
