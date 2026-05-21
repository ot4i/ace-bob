
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Microsoft SharePoint node Requirements:
1. Microsoft SharePoint Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_mssharepoint.msgnode and an attribute applicationConnectorType="mssharepoint"
2. Microsoft SharePoint Input nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_mssharepoint.msgnode and an attribute applicationConnectorType="mssharepoint"
3. The Microsoft SharePoint Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.MicrosoftSharePoint_Request" where "MessageFlowName" is the name of the message flow and where "MicrosoftSharePoint_Request" is the type of the message flow node
4. In the ACE Toolkit Application project where the message flow containing the Microsoft SharePoint Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. In the ACE Toolkit Application project where the message flow containing the Microsoft SharePoint Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
6. The Microsoft SharePoint Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:MicrosoftSharePoint1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "MicrosoftSharePoint1" is the name of a .policyxml file in the policy project.
7. For Microsoft SharePoint Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Retrieve all folders" action="RETRIEVEALL" businessObject="FolderCollection"
  -  displayName="Retrieve all files" action="RETRIEVEALL" businessObject="FileCollection"
  -  displayName="Retrieve all sites" action="RETRIEVEALL" businessObject="SiteCollection"
  -  displayName="Retrieve all lists" action="RETRIEVEALL" businessObject="ListCollection"
  -  displayName="Retrieve all list items" action="RETRIEVEALL" businessObject="ListItemCollection"
  -  displayName="Retrieve all list item attachments" action="RETRIEVEALL" businessObject="ListItemAttachmentCollection"
  -  displayName="Create file" action="CREATE" businessObject="File"
  -  displayName="Retrieve files" action="RETRIEVEALL" businessObject="File"
  -  displayName="Delete file" action="DELETEALL" businessObject="File"
  -  displayName="Update file" action="UPDATEALL" businessObject="File"
  -  displayName="Download file" action="DOWNLOADFILE" businessObject="File"
  -  displayName="Rename file" action="RENAMEFILE" businessObject="File"
  -  displayName="Share file" action="SHAREFILE" businessObject="File"
  -  displayName="Create folder" action="CREATE" businessObject="Folder"
  -  displayName="Retrieve folders" action="RETRIEVEALL" businessObject="Folder"
  -  displayName="Delete folder" action="DELETEALL" businessObject="Folder"
  -  displayName="Update folder" action="UPDATEALL" businessObject="Folder"
  -  displayName="Create site" action="CREATE" businessObject="Site"
  -  displayName="Retrieve sites" action="RETRIEVEALL" businessObject="Site"
  -  displayName="Delete site" action="DELETEALL" businessObject="Site"
  -  displayName="Update site" action="UPDATEALL" businessObject="Site"
  -  displayName="Create list" action="CREATE" businessObject="List"
  -  displayName="Retrieve lists" action="RETRIEVEALL" businessObject="List"
  -  displayName="Delete list" action="DELETEALL" businessObject="List"
  -  displayName="Update list" action="UPDATEALL" businessObject="List"
  -  displayName="Create list item" action="CREATE" businessObject="ListItem"
  -  displayName="Retrieve list items" action="RETRIEVEALL" businessObject="ListItem"
  -  displayName="Delete list item" action="DELETEALL" businessObject="ListItem"
  -  displayName="Update list item" action="UPDATEALL" businessObject="ListItem"
  -  displayName="Create list item attachment" action="CREATE" businessObject="ListItemAttachment"
  -  displayName="Retrieve all the list item attachments" action="RETRIEVEALL" businessObject="ListItemAttachment"
  -  displayName="Delete all the list item attachments" action="DELETEALL" businessObject="ListItemAttachment"
  -  displayName="Update list item attachment" action="UPDATEALL" businessObject="ListItemAttachment"
  -  displayName="Download list item attachment" action="DOWNLOADLISTITEMATTACHMENT" businessObject="ListItemAttachment"
  -  displayName="Retrieve all the folder items" action="RETRIEVEALL" businessObject="FolderItem"
  -  displayName="Retrieve users" action="RETRIEVEALL" businessObject="User"
  -  displayName="Retrieve Acl" action="RETRIEVEALL" businessObject="Acl"
  -  displayName="Retrieve shared links" action="RETRIEVEALL" businessObject="SharedLinks"
  -  displayName="Search files" action="RETRIEVEALL" businessObject="SearchFiles"
  
## Policy Project Requirements

1. Microsoft SharePoint policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "MicrosoftSharePoint_Request1". Here is an example Microsoft SharePoint policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="MicrosoftSharePoint1" policyTemplate="online_v1_basic_oauth" policyType="mssharepoint" shortDescription="" version="">
        <credentialName>MicrosoftSharePointCredential</credentialName>
        <applicationVersion>2019</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <endpointUrl>https://YourSharePointHost:8443</endpointUrl>
        <siteCollectionUrl/>
        <domainName/>
        <workstationName/>
        <proxyId/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   
