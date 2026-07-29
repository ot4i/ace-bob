# Salesforce

## Purpose
Connector-specific rules for Salesforce Request and Input nodes.

## When to use
Use this document when the requested ACE flow includes a Salesforce Request node or Salesforce Input node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- Salesforce Request node
- Salesforce Input node

## Required node attributes
### Salesforce Request
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_salesforce.msgnode`
- `applicationConnectorType="salesforce"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

### Salesforce Input
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorInput_salesforce.msgnode`
- `applicationConnectorType="salesforce"`

## Schema file requirements
For Salesforce Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
The following combinations are allowed for Salesforce Request nodes:

- `displayName="Retrieve contents of attachment"` `action="DOWNLOADCONTENT"` `businessObject="Attachment"`
- `displayName="Retrieve contents of content document"` `action="DOWNLOADDOCUMENTCONTENT"` `businessObject="ContentDocument"`
- `displayName="Create account"` `action="CREATE"` `businessObject="Account"`
- `displayName="Retrieve accounts"` `action="RETRIEVEALL"` `businessObject="Account"`
- `displayName="Retrieve account"` `action="RETRIEVE"` `businessObject="Account"`
- `displayName="Update account"` `action="UPDATE"` `businessObject="Account"`
- `displayName="Delete account"` `action="DELETEALL"` `businessObject="Account"`
- `displayName="Update account"` `action="UPDATEALL"` `businessObject="Account"`
- `displayName="Update or create account"` `action="UPSERTWITHWHERE"` `businessObject="Account"`
- `displayName="New account"` `action="CREATED"` `businessObject="Account"`
- `displayName="Updated account"` `action="UPDATED"` `businessObject="Account"`
- `displayName="Create bulk accounts"` `action="BULKCREATE"` `businessObject="Account"`
- `displayName="Update bulk accounts"` `action="BULKUPDATE"` `businessObject="Account"`
- `displayName="Delete bulk accounts"` `action="BULKDELETE"` `businessObject="Account"`
- `displayName="Create contact"` `action="CREATE"` `businessObject="Contact"`
- `displayName="Retrieve contacts"` `action="RETRIEVEALL"` `businessObject="Contact"`
- `displayName="Retrieve contact"` `action="RETRIEVE"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATE"` `businessObject="Contact"`
- `displayName="Delete contact"` `action="DELETEALL"` `businessObject="Contact"`
- `displayName="Update contact"` `action="UPDATEALL"` `businessObject="Contact"`
- `displayName="Update or create contact"` `action="UPSERTWITHWHERE"` `businessObject="Contact"`
- `displayName="New contact"` `action="CREATED"` `businessObject="Contact"`
- `displayName="Updated contact"` `action="UPDATED"` `businessObject="Contact"`
- `displayName="Create bulk contacts"` `action="BULKCREATE"` `businessObject="Contact"`
- `displayName="Update bulk contacts"` `action="BULKUPDATE"` `businessObject="Contact"`
- `displayName="Delete bulk contacts"` `action="BULKDELETE"` `businessObject="Contact"`
- `displayName="Create lead"` `action="CREATE"` `businessObject="Lead"`
- `displayName="Retrieve leads"` `action="RETRIEVEALL"` `businessObject="Lead"`
- `displayName="Retrieve lead"` `action="RETRIEVE"` `businessObject="Lead"`
- `displayName="Update lead"` `action="UPDATE"` `businessObject="Lead"`
- `displayName="Delete lead"` `action="DELETEALL"` `businessObject="Lead"`
- `displayName="Update lead"` `action="UPDATEALL"` `businessObject="Lead"`
- `displayName="Update or create lead"` `action="UPSERTWITHWHERE"` `businessObject="Lead"`
- `displayName="New lead"` `action="CREATED"` `businessObject="Lead"`
- `displayName="Updated lead"` `action="UPDATED"` `businessObject="Lead"`
- `displayName="Create bulk leads"` `action="BULKCREATE"` `businessObject="Lead"`
- `displayName="Update bulk leads"` `action="BULKUPDATE"` `businessObject="Lead"`
- `displayName="Delete bulk leads"` `action="BULKDELETE"` `businessObject="Lead"`
- `displayName="Convert lead"` `action="CONVERTLEAD"` `businessObject="Lead"`
- `displayName="Create opportunity"` `action="CREATE"` `businessObject="Opportunity"`
- `displayName="Retrieve opportunities"` `action="RETRIEVEALL"` `businessObject="Opportunity"`
- `displayName="Retrieve opportunity"` `action="RETRIEVE"` `businessObject="Opportunity"`
- `displayName="Update opportunity"` `action="UPDATE"` `businessObject="Opportunity"`
- `displayName="Delete opportunity"` `action="DELETEALL"` `businessObject="Opportunity"`
- `displayName="Update opportunity"` `action="UPDATEALL"` `businessObject="Opportunity"`
- `displayName="Update or create opportunity"` `action="UPSERTWITHWHERE"` `businessObject="Opportunity"`
- `displayName="New opportunity"` `action="CREATED"` `businessObject="Opportunity"`
- `displayName="Updated opportunity"` `action="UPDATED"` `businessObject="Opportunity"`
- `displayName="Create bulk opportunities"` `action="BULKCREATE"` `businessObject="Opportunity"`
- `displayName="Update bulk opportunities"` `action="BULKUPDATE"` `businessObject="Opportunity"`
- `displayName="Delete bulk opportunities"` `action="BULKDELETE"` `businessObject="Opportunity"`
- `displayName="Create case"` `action="CREATE"` `businessObject="Case"`
- `displayName="Retrieve cases"` `action="RETRIEVEALL"` `businessObject="Case"`
- `displayName="Retrieve case"` `action="RETRIEVE"` `businessObject="Case"`
- `displayName="Update case"` `action="UPDATE"` `businessObject="Case"`
- `displayName="Delete case"` `action="DELETEALL"` `businessObject="Case"`
- `displayName="Update case"` `action="UPDATEALL"` `businessObject="Case"`
- `displayName="Update or create case"` `action="UPSERTWITHWHERE"` `businessObject="Case"`
- `displayName="New case"` `action="CREATED"` `businessObject="Case"`
- `displayName="Updated case"` `action="UPDATED"` `businessObject="Case"`
- `displayName="Create bulk cases"` `action="BULKCREATE"` `businessObject="Case"`
- `displayName="Update bulk cases"` `action="BULKUPDATE"` `businessObject="Case"`
- `displayName="Delete bulk cases"` `action="BULKDELETE"` `businessObject="Case"`
- `displayName="Create campaign"` `action="CREATE"` `businessObject="Campaign"`
- `displayName="Retrieve campaigns"` `action="RETRIEVEALL"` `businessObject="Campaign"`
- `displayName="Retrieve campaign"` `action="RETRIEVE"` `businessObject="Campaign"`
- `displayName="Update campaign"` `action="UPDATE"` `businessObject="Campaign"`
- `displayName="Delete campaign"` `action="DELETEALL"` `businessObject="Campaign"`
- `displayName="Update campaign"` `action="UPDATEALL"` `businessObject="Campaign"`
- `displayName="Update or create campaign"` `action="UPSERTWITHWHERE"` `businessObject="Campaign"`
- `displayName="New campaign"` `action="CREATED"` `businessObject="Campaign"`
- `displayName="Updated campaign"` `action="UPDATED"` `businessObject="Campaign"`
- `displayName="Create bulk campaigns"` `action="BULKCREATE"` `businessObject="Campaign"`
- `displayName="Update bulk campaigns"` `action="BULKUPDATE"` `businessObject="Campaign"`
- `displayName="Delete bulk campaigns"` `action="BULKDELETE"` `businessObject="Campaign"`
- `displayName="Create order"` `action="CREATE"` `businessObject="Order"`
- `displayName="Retrieve orders"` `action="RETRIEVEALL"` `businessObject="Order"`
- `displayName="Retrieve order"` `action="RETRIEVE"` `businessObject="Order"`
- `displayName="Update order"` `action="UPDATE"` `businessObject="Order"`
- `displayName="Delete order"` `action="DELETEALL"` `businessObject="Order"`
- `displayName="Update order"` `action="UPDATEALL"` `businessObject="Order"`
- `displayName="Update or create order"` `action="UPSERTWITHWHERE"` `businessObject="Order"`
- `displayName="New order"` `action="CREATED"` `businessObject="Order"`
- `displayName="Create bulk orders"` `action="BULKCREATE"` `businessObject="Order"`
- `displayName="Update bulk orders"` `action="BULKUPDATE"` `businessObject="Order"`
- `displayName="Delete bulk orders"` `action="BULKDELETE"` `businessObject="Order"`
- `displayName="Create folder"` `action="CREATE"` `businessObject="Folder"`
- `displayName="Retrieve folders"` `action="RETRIEVEALL"` `businessObject="Folder"`
- `displayName="Retrieve folder"` `action="RETRIEVE"` `businessObject="Folder"`
- `displayName="Update folder"` `action="UPDATE"` `businessObject="Folder"`
- `displayName="Delete folder"` `action="DELETEALL"` `businessObject="Folder"`
- `displayName="Update folder"` `action="UPDATEALL"` `businessObject="Folder"`
- `displayName="Update or create folder"` `action="UPSERTWITHWHERE"` `businessObject="Folder"`
- `displayName="New folder"` `action="CREATED"` `businessObject="Folder"`
- `displayName="Create bulk folders"` `action="BULKCREATE"` `businessObject="Folder"`
- `displayName="Update bulk folders"` `action="BULKUPDATE"` `businessObject="Folder"`
- `displayName="Delete bulk folders"` `action="BULKDELETE"` `businessObject="Folder"`
- `displayName="Create product"` `action="CREATE"` `businessObject="Product2"`
- `displayName="Retrieve products"` `action="RETRIEVEALL"` `businessObject="Product2"`
- `displayName="Create solution"` `action="CREATE"` `businessObject="Solution"`
- `displayName="Retrieve solutions"` `action="RETRIEVEALL"` `businessObject="Solution"`
- `displayName="Create event"` `action="CREATE"` `businessObject="Event"`
- `displayName="Update event"` `action="UPDATE"` `businessObject="Event"`
- `displayName="Retrieve events"` `action="RETRIEVEALL"` `businessObject="Event"`
- `displayName="Delete event"` `action="DELETEALL"` `businessObject="Event"`
- `displayName="Retrieve event"` `action="RETRIEVE"` `businessObject="Event"`
- `displayName="Update or create event"` `action="UPSERTWITHWHERE"` `businessObject="Event"`
- `displayName="New event"` `action="CREATED"` `businessObject="Event"`
- `displayName="Create bulk events"` `action="BULKCREATE"` `businessObject="Event"`
- `displayName="Update bulk events"` `action="BULKUPDATE"` `businessObject="Event"`
- `displayName="Delete bulk events"` `action="BULKDELETE"` `businessObject="Event"`
- `displayName="Create file"` `action="CREATE"` `businessObject="File"`
- `displayName="Retrieve files metadata"` `action="RETRIEVEALL"` `businessObject="File"`
- `displayName="Update file metadata"` `action="UPDATEALL"` `businessObject="File"`
- `displayName="Delete file"` `action="DELETEALL"` `businessObject="File"`
- `displayName="Download file content"` `action="DOWNLOADFILECONTENT"` `businessObject="File"`
- `displayName="Delete files"` `action="DELETEBULKFILES"` `businessObject="File"`
- `displayName="Upload new file version"` `action="UPLOADNEWFILEVERSION"` `businessObject="File"`
- `displayName="Retrieve file shares"` `action="RETRIEVEALL"` `businessObject="FileShare"`
- `displayName="Share file"` `action="SHAREFILE"` `businessObject="FileShare"`
- `displayName="Run custom SOQL query"` `action="EXECUTECUSTOMSOQL"` `businessObject="Soql"`
- `displayName="Create task"` `action="CREATE"` `businessObject="Task"`
- `displayName="Retrieve tasks"` `action="RETRIEVEALL"` `businessObject="Task"`
- `displayName="Update task"` `action="UPDATE"` `businessObject="Task"`
- `displayName="Delete task"` `action="DELETEALL"` `businessObject="Task"`
- `displayName="Update task"` `action="UPDATEALL"` `businessObject="Task"`
- `displayName="Update or create task"` `action="UPSERTWITHWHERE"` `businessObject="Task"`
- `displayName="New task"` `action="CREATED"` `businessObject="Task"`
- `displayName="Updated task"` `action="UPDATED"` `businessObject="Task"`
- `displayName="Create bulk tasks"` `action="BULKCREATE"` `businessObject="Task"`
- `displayName="Update bulk tasks"` `action="BULKUPDATE"` `businessObject="Task"`
- `displayName="Delete bulk tasks"` `action="BULKDELETE"` `businessObject="Task"`
- `displayName="Retrieve server timestamp"` `action="GETSERVERTIMESTAMP"` `businessObject="ServerTimestamp"`
- `displayName="Retrieve user information"` `action="GETUSERINFO"` `businessObject="UserInfo"`
- `displayName="Reset user password"` `action="RESETPASSWORD"` `businessObject="UserInfo"`
- `displayName="Set user password"` `action="SETPASSWORD"` `businessObject="UserInfo"`
- `displayName="Merge objects"` `action="EXECUTEMERGE"` `businessObject="Merge"`
- `displayName="Run custom SOSL query"` `action="EXECUTECUSTOMSOSL"` `businessObject="Sosl"`
- `displayName="Send single email"` `action="SINGLEEMAIL"` `businessObject="Email"`
- `displayName="Send mass email"` `action="MASSEMAIL"` `businessObject="Email"`
- `displayName="Undelete records"` `action="UNDELETERECORDS"` `businessObject="Records"`

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Salesforce1`.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
  <policy longDescription="" policyName="Example" policyTemplate="online_v1_basic_jwt" policyType="salesforce" shortDescription="" version="">
    <credentialName>SalesforceCredential</credentialName>
    <applicationVersion>v1</applicationVersion>
    <applicationType>online</applicationType>
    <authenticationMethod>BASIC_JWT</authenticationMethod>
    <endpointUrl>https://login.salesforce.com/</endpointUrl>
    <domainName/>
    <proxyId/>
    <apiVersion>54.0</apiVersion>
  </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
