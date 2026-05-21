
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Microsoft Azure Blob storage node Requirements:
1. Microsoft Azure Blob storage Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azureblobstorage.msgnode and an attribute applicationConnectorType="azureblobstorage"
2. The Microsoft Azure Blob storage Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.MicrosoftAzureBlobstorage_Request" where "MessageFlowName" is the name of the message flow and where "MicrosoftAzureBlobstorage_Request" is the type of the message flow node
3. In the ACE Toolkit Application project where the message flow containing the Microsoft Azure Blob storage Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
4. In the ACE Toolkit Application project where the message flow containing the Microsoft Azure Blob storage Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. The Microsoft Azure Blob storage Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:MicrosoftAzureBlobstorage1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "MicrosoftAzureBlobstorage1" is the name of a .policyxml file in the policy project.
6. For Microsoft Azure Blob storage Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Create container" action="CREATE" businessObject="container"
  -  displayName="Retrieve containers" action="RETRIEVEALL" businessObject="container"
  -  displayName="Delete container" action="DELETEALL" businessObject="container"
  -  displayName="Set container metadata" action="SETCONTAINERMETADATA" businessObject="container"
  -  displayName="Check container exists" action="EXISTS" businessObject="container"
  -  displayName="Set container ACL" action="SETCONTAINERACL" businessObject="container"
  -  displayName="Get container ACL" action="GETCONTAINERACL" businessObject="container"
  -  displayName="Retrieve blobs" action="RETRIEVEALL" businessObject="blob"
  -  displayName="Update or create blob" action="UPSERTWITHWHERE" businessObject="blob"
  -  displayName="Delete blob" action="DELETEALL" businessObject="blob"
  -  displayName="Copy blob" action="COPYBLOB" businessObject="blob"
  -  displayName="Set blob metadata" action="SETBLOBMETADATA" businessObject="blob"
  -  displayName="Check blob exists" action="BLOBEXISTS" businessObject="blob"
  -  displayName="Download blob content" action="DOWNLOADBLOBCONTENT" businessObject="blob"
  -  displayName="Abort copy blob" action="ABORTCOPYBLOB" businessObject="blob"
  -  displayName="Create blob snapshot" action="CREATE" businessObject="snapshot"
  -  displayName="Retrieve blob snapshots" action="RETRIEVEALL" businessObject="snapshot"
  -  displayName="Delete blob snapshot" action="DELETEALL" businessObject="snapshot"
  -  displayName="Retrieve blob versions" action="RETRIEVEALL" businessObject="version"
  -  displayName="Delete blob version" action="DELETEALL" businessObject="version"
  -  displayName="Update or create page blob" action="UPSERTWITHWHERE" businessObject="pageBlob"
  -  displayName="Add page" action="APPENDPAGES" businessObject="pageBlob"
  -  displayName="Update or create append blob" action="UPSERTWITHWHERE" businessObject="appendBlob"
  -  displayName="Append block" action="APPENDBLOCK" businessObject="appendBlob"
  -  displayName="Set blob service properties" action="SETBLOBSERVICEPROPERTIES" businessObject="blobService"
  -  displayName="Get blob service properties" action="GETBLOBSERVICEPROPERTIES" businessObject="blobService"
 
## Policy Project Requirements

1. Microsoft Azure Blob storage policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "MicrosoftAzureBlobstorage_Request1". Here is an example Microsoft Azure Blob storage policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="MicrosoftAzureBlobstorage1" policyTemplate="online_v1_basic" policyType="azureblobstorage" shortDescription="" version="">
        <credentialName>MicrosoftAzureBlobstorageCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <accountName>YourStorageAccount</accountName>
        <tenantId/>
        <proxyId/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   

