
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## IBM Cloudant node Requirements:
1. IBM Cloudant Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_cloudantdb.msgnode and an attribute applicationConnectorType="cloudantdb"
2. The IBM Cloudant Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.IBMCloudant_Request" where "MessageFlowName" is the name of the message flow and where "IBMCloudant_Request" is the type of the message flow node
3. In the ACE Toolkit Application project where the message flow containing the IBM Cloudant Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
4. In the ACE Toolkit Application project where the message flow containing the IBM Cloudant Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. The IBM Cloudant Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:IBMCloudant1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "IBMCloudant1" is the name of a .policyxml file in the policy project.
6. For IBM Cloudant Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Create database" action="CREATE" businessObject="database"
  -  displayName="Retrieve databases" action="RETRIEVEALL" businessObject="database"
  -  displayName="Delete database" action="DELETEALL" businessObject="database"
  -  displayName="Create document" action="CREATE" businessObject="document"
  -  displayName="Retrieve documents" action="RETRIEVEALL" businessObject="document"
  -  displayName="Retrieve document" action="RETRIEVE" businessObject="document"
  -  displayName="Update document" action="UPDATEALL" businessObject="document"
  -  displayName="Update document" action="UPDATE" businessObject="document"
  -  displayName="Update or create document" action="UPSERTWITHWHERE" businessObject="document"
  -  displayName="Delete document" action="DELETEALL" businessObject="document"
  -  displayName="Create attachment" action="CREATE" businessObject="attachment"
  -  displayName="Retrieve attachments" action="RETRIEVEALL" businessObject="attachment"
  -  displayName="Retrieve attachment" action="RETRIEVE" businessObject="attachment"
  -  displayName="Update attachment" action="UPDATEALL" businessObject="attachment"
  -  displayName="Update attachment" action="UPDATE" businessObject="attachment"
  -  displayName="Update or create attachment" action="UPSERTWITHWHERE" businessObject="attachment"
  -  displayName="Delete attachment" action="DELETEALL" businessObject="attachment"
  -  displayName="Retrieve design documents" action="RETRIEVEALL" businessObject="design_document"
  -  displayName="Retrieve views" action="RETRIEVEALL" businessObject="view"
  -  displayName="Apply view" action="APPLYVIEW" businessObject="view"

## Policy Project Requirements

1. IBM Cloudant policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "IBMCloudant_Request1". Here is an example IBM Cloudant policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="IBMCloudant1" policyTemplate="online_v1_basic" policyType="cloudantdb" shortDescription="" version="">
        <credentialName>IBMCloudantCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <hostname/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   
