
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Dropbox node Requirements:
1. Dropbox Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_dropbox.msgnode and an attribute applicationConnectorType="dropbox"
2. The Dropbox Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.Dropbox_Request" where "MessageFlowName" is the name of the message flow and where "Dropbox_Request" is the type of the message flow node
3. In the ACE Toolkit Application project where the message flow containing the Dropbox Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
4. In the ACE Toolkit Application project where the message flow containing the Dropbox Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. The Dropbox Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:Dropbox1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "Dropbox1" is the name of a .policyxml file in the policy project.
6. For Dropbox Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Create Team Group" action="CREATE" businessObject="teamgroups"
  -  displayName="Retrieve all team groups" action="RETRIEVEALL" businessObject="teamgroups"
  -  displayName="Updates a group's name and/or external ID." action="UPDATEALL" businessObject="teamgroups"
  -  displayName="Delete Teams group" action="DELETEALL" businessObject="teamgroups"
  -  displayName="Add Team Group Member" action="ADDGROUPMEMBERS" businessObject="teamgroups"
  -  displayName="Retrieve all team group members" action="LISTGROUPMEMBERS" businessObject="teamgroups"
  -  displayName="Delete Teams group member" action="REMOVEGROUPMEMBERS" businessObject="teamgroups"
  -  displayName="Add Team Member" action="CREATE" businessObject="teammembers"
  -  displayName="Retrieve team members" action="RETRIEVEALL" businessObject="teammembers"
  -  displayName="Delete Teams Member" action="DELETEALL" businessObject="teammembers"
  -  displayName="Namespaces List" action="RETRIEVEALL" businessObject="namespaces"
  -  displayName="Retrieve team folders" action="RETRIEVEALL" businessObject="teamfolders"
  
## Policy Project Requirements

1. Dropbox policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "Dropbox_Request1". Here is an example Dropbox policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="Dropbox1" policyTemplate="online_v1_basic_oauth" policyType="dropbox" shortDescription="" version="">
        <credentialName>DropboxCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
        <proxyId/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   

  