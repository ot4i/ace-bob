# Mailchimp

## Purpose
Connector-specific rules for Mailchimp Request and Mailchimp Input nodes.

## When to use
Use this document when the requested ACE flow includes a Mailchimp Request node or Mailchimp Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Mailchimp Request node
- Mailchimp Input node

## Required node attributes
### Mailchimp Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_mailchimp.msgnode`
- `applicationConnectorType="mailchimp"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Mailchimp Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_mailchimp.msgnode`
- `applicationConnectorType="mailchimp"`

## Schema file requirements
For Mailchimp Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Mailchimp Request nodes:

- `displayName="Create campaign folder"` `action="CREATE"` `businessObject="CampaignFolder"`
- `displayName="Retrieve campaign folders"` `action="RETRIEVEALL"` `businessObject="CampaignFolder"`
- `displayName="Retrieve campaign folder"` `action="RETRIEVE"` `businessObject="CampaignFolder"`
- `displayName="Update campaign folder"` `action="UPDATEALL"` `businessObject="CampaignFolder"`
- `displayName="Delete campaign folder"` `action="DELETEALL"` `businessObject="CampaignFolder"`
- `displayName="Create campaign"` `action="CREATE"` `businessObject="Campaign"`
- `displayName="Retrieve campaigns"` `action="RETRIEVEALL"` `businessObject="Campaign"`
- `displayName="Retrieve campaign"` `action="RETRIEVE"` `businessObject="Campaign"`
- `displayName="Update or create campaign"` `action="UPSERT"` `businessObject="Campaign"`
- `displayName="Delete campaign"` `action="DELETEALL"` `businessObject="Campaign"`
- `displayName="Send campaign"` `action="SENDCAMPAIGN"` `businessObject="Campaign"`
- `displayName="Cancel campaign"` `action="CANCELCAMPAIGN"` `businessObject="Campaign"`
- `displayName="Update campaign content"` `action="UPDATEALL"` `businessObject="CampaignContent"`
- `displayName="Retrieve campaign content"` `action="RETRIEVEALL"` `businessObject="CampaignContent"`
- `displayName="Retrieve campaign send checklist"` `action="RETRIEVEALL"` `businessObject="CampaignSendChecklist"`
- `displayName="Create campaign feedback"` `action="CREATE"` `businessObject="CampaignFeedback"`
- `displayName="Retrieve campaign feedbacks"` `action="RETRIEVEALL"` `businessObject="CampaignFeedback"`
- `displayName="Retrieve campaign feedback"` `action="RETRIEVE"` `businessObject="CampaignFeedback"`
- `displayName="Update campaign feedback"` `action="UPDATEALL"` `businessObject="CampaignFeedback"`
- `displayName="Delete campaign feedback"` `action="DELETE"` `businessObject="CampaignFeedback"`
- `displayName="Retrieve conversations"` `action="RETRIEVEALL"` `businessObject="Conversation"`
- `displayName="Retrieve conversation"` `action="RETRIEVE"` `businessObject="Conversation"`
- `displayName="Create message"` `action="CREATE"` `businessObject="Message"`
- `displayName="Retrieve messages"` `action="RETRIEVEALL"` `businessObject="Message"`
- `displayName="Retrieve message"` `action="RETRIEVE"` `businessObject="Message"`
- `displayName="Create file manager file"` `action="CREATE"` `businessObject="FileManagerFile"`
- `displayName="Retrieve file manager files"` `action="RETRIEVEALL"` `businessObject="FileManagerFile"`
- `displayName="Retrieve file manager file"` `action="RETRIEVE"` `businessObject="FileManagerFile"`
- `displayName="Update file manager file"` `action="UPDATEALL"` `businessObject="FileManagerFile"`
- `displayName="Delete file manager file"` `action="DELETEALL"` `businessObject="FileManagerFile"`
- `displayName="Create file manager folder"` `action="CREATE"` `businessObject="FileManagerFolder"`
- `displayName="Retrieve file manager folders"` `action="RETRIEVEALL"` `businessObject="FileManagerFolder"`
- `displayName="Retrieve file manager folder"` `action="RETRIEVE"` `businessObject="FileManagerFolder"`
- `displayName="Update file manager folder"` `action="UPDATEALL"` `businessObject="FileManagerFolder"`
- `displayName="Delete file manager folder"` `action="DELETEALL"` `businessObject="FileManagerFolder"`
- `displayName="Create list"` `action="CREATE"` `businessObject="List"`
- `displayName="Retrieve lists"` `action="RETRIEVEALL"` `businessObject="List"`
- `displayName="Retrieve list"` `action="RETRIEVE"` `businessObject="List"`
- `displayName="Update or create list"` `action="UPSERT"` `businessObject="List"`
- `displayName="Delete list"` `action="DELETEALL"` `businessObject="List"`
- `displayName="Create member"` `action="CREATE"` `businessObject="Member"`
- `displayName="Retrieve members"` `action="RETRIEVEALL"` `businessObject="Member"`
- `displayName="Retrieve member"` `action="RETRIEVE"` `businessObject="Member"`
- `displayName="Update or create member"` `action="UPSERT"` `businessObject="Member"`
- `displayName="Delete member"` `action="DELETE"` `businessObject="Member"`
- `displayName="Retrieve reports"` `action="RETRIEVEALL"` `businessObject="Report"`
- `displayName="Retrieve report"` `action="RETRIEVE"` `businessObject="Report"`
- `displayName="Retrieve sent to"` `action="RETRIEVEALL"` `businessObject="SentTo"`
- `displayName="Retrieve sent to by id"` `action="RETRIEVE"` `businessObject="SentTo"`
- `displayName="Create interest category"` `action="CREATE"` `businessObject="InterestCategory"`
- `displayName="Retrieve interest categories"` `action="RETRIEVEALL"` `businessObject="InterestCategory"`
- `displayName="Retrieve interest category"` `action="RETRIEVE"` `businessObject="InterestCategory"`
- `displayName="Update interest category"` `action="UPDATEALL"` `businessObject="InterestCategory"`
- `displayName="Delete interest category"` `action="DELETE"` `businessObject="InterestCategory"`
- `displayName="Create interest"` `action="CREATE"` `businessObject="Interest"`
- `displayName="Retrieve interests"` `action="RETRIEVEALL"` `businessObject="Interest"`
- `displayName="Retrieve interest"` `action="RETRIEVE"` `businessObject="Interest"`
- `displayName="Update interest"` `action="UPDATEALL"` `businessObject="Interest"`
- `displayName="Delete interest"` `action="DELETE"` `businessObject="Interest"`
- `displayName="Retrieve segments"` `action="RETRIEVEALL"` `businessObject="Segment"`

The following combinations are allowed for Mailchimp Input nodes:

- `displayName="New member"` `action="CREATED"` `businessObject="Member"`
- `displayName="Updated member"` `action="UPDATED"` `businessObject="Member"`
- `displayName="New campaign"` `action="CREATED"` `businessObject="Campaign"`
- `displayName="Updated campaign"` `action="UPDATED"` `businessObject="Campaign"`
- `displayName="New message"` `action="CREATED"` `businessObject="Message"`
- `displayName="New list"` `action="CREATED"` `businessObject="List"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Mailchimp1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Mailchimp1" policyTemplate="online_v1_basic_oauth" policyType="mailchimp" shortDescription="" version="">
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
