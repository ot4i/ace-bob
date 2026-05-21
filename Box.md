
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Box node Requirements:
1. Box Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_box.msgnode and an attribute applicationConnectorType="box"
2. The Box Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.Box_Request" where "MessageFlowName" is the name of the message flow and where "Box_Request" is the type of the message flow node
3. In the ACE Toolkit Application project where the message flow containing the Box Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
4. In the ACE Toolkit Application project where the message flow containing the Box Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. The Box Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:Box1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "Box1" is the name of a .policyxml file in the policy project.
6. For Box Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Create file" action="CREATE" businessObject="File"
  -  displayName="Retrieve file metadata" action="RETRIEVEALL" businessObject="File"
  -  displayName="Update files" action="UPDATEALL" businessObject="File"
  -  displayName="Delete files" action="DELETEALL" businessObject="File"
  -  displayName="Retrieve file content" action="DOWNLOADFILE" businessObject="File"
  -  displayName="Copy file" action="COPYFILE" businessObject="File"
  -  displayName="Retrieve trashed file" action="RETRIEVETRASHEDFILE" businessObject="File"
  -  displayName="Retrieve file versions" action="RETRIEVEALL" businessObject="FileVersions"
  -  displayName="Create folder" action="CREATE" businessObject="Folder"
  -  displayName="Retrieve folders" action="RETRIEVEALL" businessObject="Folder"
  -  displayName="Update folders" action="UPDATEALL" businessObject="Folder"
  -  displayName="Delete folders" action="DELETEALL" businessObject="Folder"
  -  displayName="Copy folder" action="COPYFOLDER" businessObject="Folder"
  -  displayName="Create bookmark" action="CREATE" businessObject="Web_Link"
  -  displayName="Retrieve bookmarks" action="RETRIEVEALL" businessObject="Web_Link"
  -  displayName="Update bookmarks" action="UPDATEALL" businessObject="Web_Link"
  -  displayName="Delete bookmarks" action="DELETEALL" businessObject="Web_Link"
  -  displayName="Retrieve folder items" action="RETRIEVEALL" businessObject="FolderItem"
  -  displayName="Create group" action="CREATE" businessObject="Group"
  -  displayName="Retrieve groups" action="RETRIEVE" businessObject="Group"
  -  displayName="Retrieve groups" action="RETRIEVEALL" businessObject="Group"
  -  displayName="Update groups" action="UPDATEALL" businessObject="Group"
  -  displayName="Delete groups" action="DELETEALL" businessObject="Group"
  -  displayName="Create user" action="CREATE" businessObject="User"
  -  displayName="Update users" action="UPDATEALL" businessObject="User"
  -  displayName="Retrieve users" action="RETRIEVE" businessObject="User"
  -  displayName="Retrieve users" action="RETRIEVEALL" businessObject="User"
  -  displayName="Delete users" action="DELETEALL" businessObject="User"
  -  displayName="Create comment" action="CREATE" businessObject="Comment"
  -  displayName="Retrieve comments" action="RETRIEVEALL" businessObject="Comment"
  -  displayName="Update comments" action="UPDATEALL" businessObject="Comment"
  -  displayName="Delete comments" action="DELETEALL" businessObject="Comment"
  -  displayName="Create task" action="CREATE" businessObject="Task"
  -  displayName="Retrieve tasks" action="RETRIEVEALL" businessObject="Task"
  -  displayName="Update tasks" action="UPDATEALL" businessObject="Task"
  -  displayName="Delete tasks" action="DELETEALL" businessObject="Task"
  -  displayName="Create group membership" action="CREATE" businessObject="GroupMembership"
  -  displayName="Retrieve group memberships" action="RETRIEVEALL" businessObject="GroupMembership"
  -  displayName="Update group memberships" action="UPDATEALL" businessObject="GroupMembership"
  -  displayName="Delete group memberships" action="DELETEALL" businessObject="GroupMembership"
  -  displayName="Create task assignment" action="CREATE" businessObject="TaskAssignment"
  -  displayName="Retrieve task assignments" action="RETRIEVEALL" businessObject="TaskAssignment"
  -  displayName="Update task assignments" action="UPDATEALL" businessObject="TaskAssignment"
  -  displayName="Delete task assignments" action="DELETEALL" businessObject="TaskAssignment"
  -  displayName="Create collaboration" action="CREATE" businessObject="Collaboration"
  -  displayName="Retrieve collaborations" action="RETRIEVEALL" businessObject="Collaboration"
  -  displayName="Update collaborations" action="UPDATEALL" businessObject="Collaboration"
  -  displayName="Delete collaborations" action="DELETEALL" businessObject="Collaboration"
  -  displayName="Retrieve shared links" action="RETRIEVEALL" businessObject="SharedLink"
  -  displayName="Create or update shared link" action="UPSERTSHAREDLINK" businessObject="SharedLink"

## Policy Project Requirements

1. Box policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "Box_Request1". Here is an example Box policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="Box1" policyTemplate="admin_v1_basic_oauth" policyType="box" shortDescription="" version="">
        <credentialName>BoxCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>admin</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   

