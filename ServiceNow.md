
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## ServiceNow node Requirements:
1. ServiceNow Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_servicenow.msgnode and an attribute applicationConnectorType="servicenow"
2. ServiceNow Input nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_servicenow.msgnode and an attribute applicationConnectorType="servicenow"
3. The ServiceNow Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.ServiceNow_Request" where "MessageFlowName" is the name of the message flow and where "ServiceNow_Request" is the type of the message flow node
4. In the ACE Toolkit Application project where the message flow containing the ServiceNow Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. In the ACE Toolkit Application project where the message flow containing the ServiceNow Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
6. The ServiceNow Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:ServiceNow1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "ServiceNow1" is the name of a .policyxml file in the policy project.
7. For ServiceNow Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Create incident" action="CREATE" businessObject="incident"
  -  displayName="Update incident" action="UPDATE" businessObject="incident"
  -  displayName="Update incidents" action="UPDATEALL" businessObject="incident"
  -  displayName="Retrieve incident" action="RETRIEVE" businessObject="incident"
  -  displayName="Retrieve incidents" action="RETRIEVEALL" businessObject="incident"
  -  displayName="Delete incidents" action="DELETEALL" businessObject="incident"
  -  displayName="Update or create incident" action="UPSERTWITHWHERE" businessObject="incident"
  -  displayName="New incident" action="CREATED" businessObject="incident"
  -  displayName="Updated incident" action="UPDATED" businessObject="incident"
  -  displayName="Create asset" action="CREATE" businessObject="alm_asset"
  -  displayName="Update asset" action="UPDATE" businessObject="alm_asset"
  -  displayName="Update assets" action="UPDATEALL" businessObject="alm_asset"
  -  displayName="Retrieve asset" action="RETRIEVE" businessObject="alm_asset"
  -  displayName="Retrieve assets" action="RETRIEVEALL" businessObject="alm_asset"
  -  displayName="Delete assets" action="DELETEALL" businessObject="alm_asset"
  -  displayName="Update or create asset" action="UPSERTWITHWHERE" businessObject="alm_asset"
  -  displayName="New asset" action="CREATED" businessObject="alm_asset"
  -  displayName="Updated asset" action="UPDATED" businessObject="alm_asset"
  -  displayName="Create department" action="CREATE" businessObject="cmn_department"
  -  displayName="Update department" action="UPDATE" businessObject="cmn_department"
  -  displayName="Update departments" action="UPDATEALL" businessObject="cmn_department"
  -  displayName="Retrieve department" action="RETRIEVE" businessObject="cmn_department"
  -  displayName="Retrieve departments" action="RETRIEVEALL" businessObject="cmn_department"
  -  displayName="Delete departments" action="DELETEALL" businessObject="cmn_department"
  -  displayName="Update or create department" action="UPSERTWITHWHERE" businessObject="cmn_department"
  -  displayName="New department" action="CREATED" businessObject="cmn_department"
  -  displayName="Updated department" action="UPDATED" businessObject="cmn_department"
  -  displayName="Create problem" action="CREATE" businessObject="problem"
  -  displayName="Update problem" action="UPDATE" businessObject="problem"
  -  displayName="Update problems" action="UPDATEALL" businessObject="problem"
  -  displayName="Retrieve problem" action="RETRIEVE" businessObject="problem"
  -  displayName="Retrieve problems" action="RETRIEVEALL" businessObject="problem"
  -  displayName="Delete problems" action="DELETEALL" businessObject="problem"
  -  displayName="Update or create problem" action="UPSERTWITHWHERE" businessObject="problem"
  -  displayName="New problem" action="CREATED" businessObject="problem"
  -  displayName="Updated problem" action="UPDATED" businessObject="problem"
  -  displayName="Create ticket" action="CREATE" businessObject="ticket"
  -  displayName="Update ticket" action="UPDATE" businessObject="ticket"
  -  displayName="Update tickets" action="UPDATEALL" businessObject="ticket"
  -  displayName="Retrieve ticket" action="RETRIEVE" businessObject="ticket"
  -  displayName="Retrieve tickets" action="RETRIEVEALL" businessObject="ticket"
  -  displayName="Delete tickets" action="DELETEALL" businessObject="ticket"
  -  displayName="Update or create ticket" action="UPSERTWITHWHERE" businessObject="ticket"
  -  displayName="New ticket" action="CREATED" businessObject="ticket"
  -  displayName="Updated ticket" action="UPDATED" businessObject="ticket"
  -  displayName="Create system user" action="CREATE" businessObject="sys_user"
  -  displayName="Update system user" action="UPDATE" businessObject="sys_user"
  -  displayName="Updates system users" action="UPDATEALL" businessObject="sys_user"
  -  displayName="Retrieve system user" action="RETRIEVE" businessObject="sys_user"
  -  displayName="Retrieve system users" action="RETRIEVEALL" businessObject="sys_user"
  -  displayName="Delete system users" action="DELETEALL" businessObject="sys_user"
  -  displayName="Update or create system user" action="UPSERTWITHWHERE" businessObject="sys_user"
  -  displayName="New system user" action="CREATED" businessObject="sys_user"
  -  displayName="Updated system user" action="UPDATED" businessObject="sys_user"
  -  displayName="Create attachment" action="CREATE" businessObject="sys_attachment"
  -  displayName="Update attachment" action="UPDATE" businessObject="sys_attachment"
  -  displayName="Retrieve attachment" action="RETRIEVE" businessObject="sys_attachment"
  -  displayName="Retrieve attachments" action="RETRIEVEALL" businessObject="sys_attachment"
  -  displayName="Update or create attachment" action="UPSERTWITHWHERE" businessObject="sys_attachment"
  -  displayName="Download File Attachment Content" action="DOWNLOADATTACHMENT" businessObject="sys_attachment"
  -  displayName="New attachment" action="CREATED" businessObject="sys_attachment"
  -  displayName="Create comment" action="CREATE" businessObject="sys_journal_field"
  -  displayName="Update comment" action="UPDATE" businessObject="sys_journal_field"
  -  displayName="Update comments" action="UPDATEALL" businessObject="sys_journal_field"
  -  displayName="Retrieve comment" action="RETRIEVE" businessObject="sys_journal_field"
  -  displayName="Retrieve comments" action="RETRIEVEALL" businessObject="sys_journal_field"
  -  displayName="Update or create comment" action="UPSERTWITHWHERE" businessObject="sys_journal_field"
  -  displayName="New comment" action="CREATED" businessObject="sys_journal_field"
  -  displayName="Create knowledge" action="CREATE" businessObject="kb_knowledge"
  -  displayName="Update knowledge" action="UPDATE" businessObject="kb_knowledge"
  -  displayName="Update knowledge" action="UPDATEALL" businessObject="kb_knowledge"
  -  displayName="Retrieve knowledge" action="RETRIEVEALL" businessObject="kb_knowledge"
  -  displayName="Update or create knowledge" action="UPSERTWITHWHERE" businessObject="kb_knowledge"
  -  displayName="Delete knowledge" action="DELETEALL" businessObject="kb_knowledge"
  -  displayName="Download knowledge article attachment" action="DOWNLOADARTICLEATTACHMENT" businessObject="kb_knowledge_article"
  -  displayName="Get additional knowledge metadata" action="GETKNOWLEDGEARTICLEDETAILS" businessObject="kb_knowledge_article"

## Policy Project Requirements

1. ServiceNow policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "ServiceNow_Request1". Here is an example ServiceNow policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
	  <policy longDescription="" policyName="Example" policyTemplate="online_v1_basic" policyType="servicenow" shortDescription="" version="">
        <credentialName>ServiceNowCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl>YourEndpointURL</endpointUrl>
        <proxyId/>
      </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   
