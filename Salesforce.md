
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Salesforce node Requirements:
1. Salesforce Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_salesforce.msgnode and an attribute applicationConnectorType="salesforce"
2. Salesforce Input nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_salesforce.msgnode and an attribute applicationConnectorType="salesforce"
3. The Salesforce Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.Salesforce_Request" where "MessageFlowName" is the name of the message flow and where "Salesforce_Request" is the type of the message flow node
4. In the ACE Toolkit Application project where the message flow containing the Salesforce Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. In the ACE Toolkit Application project where the message flow containing the Salesforce Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
6. The Salesforce Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:Salesforce1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "Salesforce1" is the name of a .policyxml file in the policy project.
7. For Salesforce Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Retrieve contents of attachment" action="DOWNLOADCONTENT" businessObject="Attachment"
  -  displayName="Retrieve contents of content document" action="DOWNLOADDOCUMENTCONTENT" businessObject="ContentDocument"
  -  displayName="Create account" action="CREATE" businessObject="Account"
  -  displayName="Retrieve accounts" action="RETRIEVEALL" businessObject="Account"
  -  displayName="Retrieve account" action="RETRIEVE" businessObject="Account"
  -  displayName="Update account" action="UPDATE" businessObject="Account"
  -  displayName="Delete account" action="DELETEALL" businessObject="Account"
  -  displayName="Update account" action="UPDATEALL" businessObject="Account"
  -  displayName="Update or create account" action="UPSERTWITHWHERE" businessObject="Account"
  -  displayName="New account" action="CREATED" businessObject="Account"
  -  displayName="Updated account" action="UPDATED" businessObject="Account"
  -  displayName="Create bulk accounts" action="BULKCREATE" businessObject="Account"
  -  displayName="Update bulk accounts" action="BULKUPDATE" businessObject="Account"
  -  displayName="Delete bulk accounts" action="BULKDELETE" businessObject="Account"
  -  displayName="Create contact" action="CREATE" businessObject="Contact"
  -  displayName="Retrieve contacts" action="RETRIEVEALL" businessObject="Contact"
  -  displayName="Retrieve contact" action="RETRIEVE" businessObject="Contact"
  -  displayName="Update contact" action="UPDATE" businessObject="Contact"
  -  displayName="Delete contact" action="DELETEALL" businessObject="Contact"
  -  displayName="Update contact" action="UPDATEALL" businessObject="Contact"
  -  displayName="Update or create contact" action="UPSERTWITHWHERE" businessObject="Contact"
  -  displayName="New contact" action="CREATED" businessObject="Contact"
  -  displayName="Updated contact" action="UPDATED" businessObject="Contact"
  -  displayName="Create bulk contacts" action="BULKCREATE" businessObject="Contact"
  -  displayName="Update bulk contacts" action="BULKUPDATE" businessObject="Contact"
  -  displayName="Delete bulk contacts" action="BULKDELETE" businessObject="Contact"
  -  displayName="Create lead" action="CREATE" businessObject="Lead"
  -  displayName="Retrieve leads" action="RETRIEVEALL" businessObject="Lead"
  -  displayName="Retrieve lead" action="RETRIEVE" businessObject="Lead"
  -  displayName="Update lead" action="UPDATE" businessObject="Lead"
  -  displayName="Delete lead" action="DELETEALL" businessObject="Lead"
  -  displayName="Update lead" action="UPDATEALL" businessObject="Lead"
  -  displayName="Update or create lead" action="UPSERTWITHWHERE" businessObject="Lead"
  -  displayName="New lead" action="CREATED" businessObject="Lead"
  -  displayName="Updated lead" action="UPDATED" businessObject="Lead"
  -  displayName="Create bulk leads" action="BULKCREATE" businessObject="Lead"
  -  displayName="Update bulk leads" action="BULKUPDATE" businessObject="Lead"
  -  displayName="Delete bulk leads" action="BULKDELETE" businessObject="Lead"
  -  displayName="Convert lead" action="CONVERTLEAD" businessObject="Lead"
  -  displayName="Create opportunity" action="CREATE" businessObject="Opportunity"
  -  displayName="Retrieve opportunities" action="RETRIEVEALL" businessObject="Opportunity"
  -  displayName="Retrieve opportunity" action="RETRIEVE" businessObject="Opportunity"
  -  displayName="Update opportunity" action="UPDATE" businessObject="Opportunity"
  -  displayName="Delete opportunity" action="DELETEALL" businessObject="Opportunity"
  -  displayName="Update opportunity" action="UPDATEALL" businessObject="Opportunity"
  -  displayName="Update or create opportunity" action="UPSERTWITHWHERE" businessObject="Opportunity"
  -  displayName="New opportunity" action="CREATED" businessObject="Opportunity"
  -  displayName="Updated opportunity" action="UPDATED" businessObject="Opportunity"
  -  displayName="Create bulk opportunities" action="BULKCREATE" businessObject="Opportunity"
  -  displayName="Update bulk opportunities" action="BULKUPDATE" businessObject="Opportunity"
  -  displayName="Delete bulk opportunities" action="BULKDELETE" businessObject="Opportunity"
  -  displayName="Create case" action="CREATE" businessObject="Case"
  -  displayName="Retrieve cases" action="RETRIEVEALL" businessObject="Case"
  -  displayName="Retrieve case" action="RETRIEVE" businessObject="Case"
  -  displayName="Update case" action="UPDATE" businessObject="Case"
  -  displayName="Delete case" action="DELETEALL" businessObject="Case"
  -  displayName="Update case" action="UPDATEALL" businessObject="Case"
  -  displayName="Update or create case" action="UPSERTWITHWHERE" businessObject="Case"
  -  displayName="New case" action="CREATED" businessObject="Case"
  -  displayName="Updated case" action="UPDATED" businessObject="Case"
  -  displayName="Create bulk cases" action="BULKCREATE" businessObject="Case"
  -  displayName="Update bulk cases" action="BULKUPDATE" businessObject="Case"
  -  displayName="Delete bulk cases" action="BULKDELETE" businessObject="Case"
  -  displayName="Create campaign" action="CREATE" businessObject="Campaign"
  -  displayName="Retrieve campaigns" action="RETRIEVEALL" businessObject="Campaign"
  -  displayName="Retrieve campaign" action="RETRIEVE" businessObject="Campaign"
  -  displayName="Update campaign" action="UPDATE" businessObject="Campaign"
  -  displayName="Delete campaign" action="DELETEALL" businessObject="Campaign"
  -  displayName="Update campaign" action="UPDATEALL" businessObject="Campaign"
  -  displayName="Update or create campaign" action="UPSERTWITHWHERE" businessObject="Campaign"
  -  displayName="New campaign" action="CREATED" businessObject="Campaign"
  -  displayName="Updated campaign" action="UPDATED" businessObject="Campaign"
  -  displayName="Create bulk campaigns" action="BULKCREATE" businessObject="Campaign"
  -  displayName="Update bulk campaigns" action="BULKUPDATE" businessObject="Campaign"
  -  displayName="Delete bulk campaigns" action="BULKDELETE" businessObject="Campaign"
  -  displayName="Create order" action="CREATE" businessObject="Order"
  -  displayName="Retrieve orders" action="RETRIEVEALL" businessObject="Order"
  -  displayName="Retrieve order" action="RETRIEVE" businessObject="Order"
  -  displayName="Update order" action="UPDATE" businessObject="Order"
  -  displayName="Delete order" action="DELETEALL" businessObject="Order"
  -  displayName="Update order" action="UPDATEALL" businessObject="Order"
  -  displayName="Update or create order" action="UPSERTWITHWHERE" businessObject="Order"
  -  displayName="New order" action="CREATED" businessObject="Order"
  -  displayName="Create bulk orders" action="BULKCREATE" businessObject="Order"
  -  displayName="Update bulk orders" action="BULKUPDATE" businessObject="Order"
  -  displayName="Delete bulk orders" action="BULKDELETE" businessObject="Order"
  -  displayName="Create folder" action="CREATE" businessObject="Folder"
  -  displayName="Retrieve folders" action="RETRIEVEALL" businessObject="Folder"
  -  displayName="Retrieve folder" action="RETRIEVE" businessObject="Folder"
  -  displayName="Update folder" action="UPDATE" businessObject="Folder"
  -  displayName="Delete folder" action="DELETEALL" businessObject="Folder"
  -  displayName="Update folder" action="UPDATEALL" businessObject="Folder"
  -  displayName="Update or create folder" action="UPSERTWITHWHERE" businessObject="Folder"
  -  displayName="New folder" action="CREATED" businessObject="Folder"
  -  displayName="Create bulk folders" action="BULKCREATE" businessObject="Folder"
  -  displayName="Update bulk folders" action="BULKUPDATE" businessObject="Folder"
  -  displayName="Delete bulk folders" action="BULKDELETE" businessObject="Folder"
  -  displayName="Create product" action="CREATE" businessObject="Product2"
  -  displayName="Retrieve products" action="RETRIEVEALL" businessObject="Product2"
  -  displayName="Create solution" action="CREATE" businessObject="Solution"
  -  displayName="Retrieve solutions" action="RETRIEVEALL" businessObject="Solution"
  -  displayName="Create event" action="CREATE" businessObject="Event"
  -  displayName="Update event" action="UPDATE" businessObject="Event"
  -  displayName="Retrieve events" action="RETRIEVEALL" businessObject="Event"
  -  displayName="Delete event" action="DELETEALL" businessObject="Event"
  -  displayName="Retrieve event" action="RETRIEVE" businessObject="Event"
  -  displayName="Update or create event" action="UPSERTWITHWHERE" businessObject="Event"
  -  displayName="New event" action="CREATED" businessObject="Event"
  -  displayName="Create bulk events" action="BULKCREATE" businessObject="Event"
  -  displayName="Update bulk events" action="BULKUPDATE" businessObject="Event"
  -  displayName="Delete bulk events" action="BULKDELETE" businessObject="Event"
  -  displayName="Create file" action="CREATE" businessObject="File"
  -  displayName="Retrieve files metadata" action="RETRIEVEALL" businessObject="File"
  -  displayName="Update file metadata" action="UPDATEALL" businessObject="File"
  -  displayName="Delete file" action="DELETEALL" businessObject="File"
  -  displayName="Download file content" action="DOWNLOADFILECONTENT" businessObject="File"
  -  displayName="Delete files" action="DELETEBULKFILES" businessObject="File"
  -  displayName="Upload new file version" action="UPLOADNEWFILEVERSION" businessObject="File"
  -  displayName="Retrieve file shares" action="RETRIEVEALL" businessObject="FileShare"
  -  displayName="Share file" action="SHAREFILE" businessObject="FileShare"
  -  displayName="Run custom SOQL query" action="EXECUTECUSTOMSOQL" businessObject="Soql"
  -  displayName="Create task" action="CREATE" businessObject="Task"
  -  displayName="Retrieve tasks" action="RETRIEVEALL" businessObject="Task"
  -  displayName="Update task" action="UPDATE" businessObject="Task"
  -  displayName="Delete task" action="DELETEALL" businessObject="Task"
  -  displayName="Update task" action="UPDATEALL" businessObject="Task"
  -  displayName="Update or create task" action="UPSERTWITHWHERE" businessObject="Task"
  -  displayName="New task" action="CREATED" businessObject="Task"
  -  displayName="Updated task" action="UPDATED" businessObject="Task"
  -  displayName="Create bulk tasks" action="BULKCREATE" businessObject="Task"
  -  displayName="Update bulk tasks" action="BULKUPDATE" businessObject="Task"
  -  displayName="Delete bulk tasks" action="BULKDELETE" businessObject="Task"
  -  displayName="Retrieve server timestamp" action="GETSERVERTIMESTAMP" businessObject="ServerTimestamp"
  -  displayName="Retrieve user information" action="GETUSERINFO" businessObject="UserInfo"
  -  displayName="Reset user password" action="RESETPASSWORD" businessObject="UserInfo"
  -  displayName="Set user password" action="SETPASSWORD" businessObject="UserInfo"
  -  displayName="Merge objects" action="EXECUTEMERGE" businessObject="Merge"
  -  displayName="Run custom SOSL query" action="EXECUTECUSTOMSOSL" businessObject="Sosl"
  -  displayName="Send single email" action="SINGLEEMAIL" businessObject="Email"
  -  displayName="Send mass email" action="MASSEMAIL" businessObject="Email"
  -  displayName="Undelete records" action="UNDELETERECORDS" businessObject="Records"
  
## Policy Project Requirements

1. Salesforce policies MUST be created in a separate Policy Project, NOT in the Application project
2. A Policy project is a specialized form of an Eclipse project
3. To be recognised as an Eclipse project, the file system directory representing the project **MUST** contain a .project file
4. ACE Policy projects **MUST** contain the following project natures section in the .project file:
   ```
   <natures>
     <nature>com.ibm.etools.mft.policy.ui.Nature</nature>
   </natures>
   ```
5. ACE Policy projects **MUST** contain the following buildSpec section in the .project file:
   ```
   <buildSpec>
     <buildCommand>
       <name>com.ibm.etools.mft.policy.ui.policybuilder</name>
       <arguments>
       </arguments>
     </buildCommand>
   </buildSpec>
   ```	 
6. The Eclipse project **MUST** be created with a .settings subdirectory. The .settings folder **MUST** contain a file named org.eclipse.core.resources.prefs which should contain the following:
   ```
   eclipse.preferences.version=1
   encoding/<project>=UTF-8
   ```
7. In order to make the Eclipse project an ACE Policy project it **MUST** have a policy.descriptor file in the root of the project directory. This file has a fixed name policy.descriptor. The content of the policy.descriptor looks like this:
   ```
   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <ns2:policyProjectDescriptor xmlns="http://com.ibm.etools.mft.descriptor.base" xmlns:ns2="http://com.ibm.etools.mft.descriptor.policyProject">
     <references/>
   </ns2:policyProjectDescriptor>
   ```
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "Salesforce_Request1". Here is an example Salesforce policy:
   ```
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
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   


    
     


	

