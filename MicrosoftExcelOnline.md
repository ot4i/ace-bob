
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Microsoft Excel Online node Requirements:
1. Microsoft Excel Online Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msexcel.msgnode and an attribute applicationConnectorType="msexcel"
2. Microsoft Excel Online Input nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_msexcel.msgnode and an attribute applicationConnectorType="msexcel"
3. The Microsoft Excel Online Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.MicrosoftExcelOnline_Request" where "MessageFlowName" is the name of the message flow and where "MicrosoftExcelOnline_Request" is the type of the message flow node
4. In the ACE Toolkit Application project where the message flow containing the Microsoft Excel Online Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. In the ACE Toolkit Application project where the message flow containing the Microsoft Excel Online Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
6. The Microsoft Excel Online Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:MicrosoftExcelOnline1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "MicrosoftExcelOnline1" is the name of a .policyxml file in the policy project.
7. For Microsoft Excel Online Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Insert row" action="CREATE" businessObject="Row"
  -  displayName="Retrieve rows" action="RETRIEVEALL" businessObject="Row"
  -  displayName="Delete row" action="DELETEALL" businessObject="Row"
  -  displayName="Update row" action="UPDATEALL" businessObject="Row"
  -  displayName="Append row" action="APPENDROW" businessObject="Row"
  -  displayName="New row appended" action="CREATED" businessObject="Row"
  -  displayName="Retrieve drives" action="RETRIEVEALL" businessObject="Drive"
  -  displayName="Create workbook" action="CREATE" businessObject="Workbook"
  -  displayName="Retrieve workbooks" action="RETRIEVEALL" businessObject="Workbook"
  -  displayName="Delete workbook" action="DELETEALL" businessObject="Workbook"
  -  displayName="Rename workbook" action="UPDATEALL" businessObject="Workbook"
  -  displayName="Download workbook" action="DOWNLOADWORKBOOK" businessObject="Workbook"
  -  displayName="Upload workbook" action="UPLOADWORKBOOK" businessObject="Workbook"
  -  displayName="Create worksheet" action="CREATE" businessObject="Worksheet"
  -  displayName="Retrieve worksheets" action="RETRIEVEALL" businessObject="Worksheet"
  -  displayName="Delete worksheet" action="DELETEALL" businessObject="Worksheet"
  -  displayName="Rename worksheet" action="UPDATEALL" businessObject="Worksheet"
  -  displayName="Create table" action="CREATE" businessObject="Table"
  -  displayName="Retrieve tables" action="RETRIEVEALL" businessObject="Table"
  -  displayName="Delete table" action="DELETEALL" businessObject="Table"
  -  displayName="Update table" action="UPDATEALL" businessObject="Table"
  -  displayName="Retrieve column data" action="RETRIEVEALL" businessObject="Column"
  -  displayName="Append table row" action="CREATE" businessObject="Tablerow"
  -  displayName="Retrieve table rows" action="RETRIEVEALL" businessObject="Tablerow"
  -  displayName="Delete table row" action="DELETEALL" businessObject="Tablerow"
  -  displayName="Update table row" action="UPDATEALL" businessObject="Tablerow"
  -  displayName="New table row appended" action="CREATED" businessObject="Tablerow"
  -  displayName="Retrieve cell ranges" action="RETRIEVEALL" businessObject="Range"
    
## Policy Project Requirements

1. Microsoft Excel Online policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "MicrosoftExcelOnline_Request1". Here is an example Microsoft Excel Online policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="MicrosoftExcelOnline1" policyTemplate="online_v1_basic_oauth" policyType="msexcel" shortDescription="" version="">
        <credentialName>MicrosoftExcelOnlineCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC_OAUTH</authenticationMethod>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   
