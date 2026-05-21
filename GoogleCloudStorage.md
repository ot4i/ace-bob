
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Google Cloud Storage node Requirements:
1. Google Cloud Storage Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlecloudstorage.msgnode and an attribute applicationConnectorType="googlecloudstorage"
2. The Google Cloud Storage Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.GoogleCloudStorage_Request" where "MessageFlowName" is the name of the message flow and where "GoogleCloudStorage_Request" is the type of the message flow node
3. In the ACE Toolkit Application project where the message flow containing the Google Cloud Storage Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
4. In the ACE Toolkit Application project where the message flow containing the Google Cloud Storage Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. The Google Cloud Storage Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:GoogleCloudStorage1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "GoogleCloudStorage1" is the name of a .policyxml file in the policy project.
6. For Google Cloud Storage Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Create bucket" action="CREATE" businessObject="Bucket"
  -  displayName="Retrieve buckets" action="RETRIEVEALL" businessObject="Bucket"
  -  displayName="Delete bucket" action="DELETEALL" businessObject="Bucket"
  -  displayName="Set bucket default storage class" action="SETBUCKETDEFAULTSTORAGECLASS" businessObject="Bucket"
  -  displayName="Get bucket default storage class" action="GETBUCKETDEFAULTSTORAGECLASS" businessObject="Bucket"
  -  displayName="Retrieve bucket ACLs" action="RETRIEVEALL" businessObject="BucketACL"
  -  displayName="Update bucket ACL" action="UPDATEBUCKETACL" businessObject="BucketACL"
  -  displayName="Get bucket tags" action="GETBUCKETTAGS" businessObject="BucketTags"
  -  displayName="Set bucket tags" action="SETBUCKETTAGS" businessObject="BucketTags"
  -  displayName="Retrieve bucket lifecycle configurations" action="RETRIEVEALL" businessObject="BucketLifecycleConfiguration"
  -  displayName="Update bucket lifecycle configuration" action="UPDATEBUCKETLIFECYCLECONFIG" businessObject="BucketLifecycleConfiguration"
  -  displayName="Get bucket versioning" action="GETBUCKETVERSIONING" businessObject="BucketVersioning"
  -  displayName="Set bucket versioning" action="SETBUCKETVERSIONING" businessObject="BucketVersioning"
  -  displayName="Retrieve bucket CORS configurations" action="RETRIEVEALL" businessObject="BucketCORSConfiguration"
  -  displayName="Update bucket CORS configuration" action="UPDATEBUCKETCORSCONFIG" businessObject="BucketCORSConfiguration"
  -  displayName="Retrieve bucket logging configurations" action="RETRIEVEALL" businessObject="BucketLoggingConfiguration"
  -  displayName="Update bucket logging configuration" action="UPDATEBUCKETLOGGINGCONFIGURATION" businessObject="BucketLoggingConfiguration"
  -  displayName="Retrieve bucket website" action="RETRIEVEALL" businessObject="BucketWebsite"
  -  displayName="Update bucket website" action="UPDATEBUCKETWEBSITE" businessObject="BucketWebsite"
  -  displayName="Retrieve bucket location" action="RETRIEVEALL" businessObject="BucketLocation"
  -  displayName="Retrieve objects" action="RETRIEVEALL" businessObject="Object"
  -  displayName="Update or create object" action="UPSERTWITHWHERE" businessObject="Object"
  -  displayName="Delete object" action="DELETEALL" businessObject="Object"
  -  displayName="Copy object" action="COPYOBJECT" businessObject="Object"
  -  displayName="Download object content" action="DOWNLOADOBJECTCONTENT" businessObject="Object"
  -  displayName="Retrieve object ACL" action="RETRIEVEALL" businessObject="ObjectACL"
  -  displayName="Update object ACL" action="UPDATEOBJECTACL" businessObject="ObjectACL"
  -  displayName="Retrieve object versioning" action="RETRIEVEALL" businessObject="ObjectVersioning"
  
## Policy Project Requirements

1. Google Cloud Storage policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "GoogleCloudStorage_Request1". Here is an example Google Cloud Storage policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="GoogleCloudStorage1" policyTemplate="online_v1_basic" policyType="googlecloudstorage" shortDescription="" version="">
        <credentialName>GoogleCloudStorageCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <bucketName/>
        <proxyId/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   

    