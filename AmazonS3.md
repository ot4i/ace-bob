
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Amazon S3 node Requirements:
1. Amazon S3 Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazons3.msgnode and an attribute applicationConnectorType="amazons3"
2. The Amazon S3 Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.AmazonS3_Request" where "MessageFlowName" is the name of the message flow and where "AmazonS3_Request" is the type of the message flow node
3. In the ACE Toolkit Application project where the message flow containing the Amazon S3 Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
4. In the ACE Toolkit Application project where the message flow containing the Amazon S3 Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. The Amazon S3 Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:AmazonS31" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "AmazonS31" is the name of a .policyxml file in the policy project.
6. For Amazon S3 Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Retrieve all buckets" action="RETRIEVEALL" businessObject="bucketcollection"
  -  displayName="Retrieve all objects" action="RETRIEVEALL" businessObject="objectcollection"
  -  displayName="Update or create object" action="UPSERTWITHWHERE" businessObject="object"
  -  displayName="Delete object" action="DELETEALL" businessObject="object"
  -  displayName="Retrieve object metadata" action="RETRIEVEALL" businessObject="object"
  -  displayName="Retrieve object content" action="DOWNLOAD_OBJECT" businessObject="object"
  -  displayName="Copy object" action="COPY_OBJECT" businessObject="object"
  -  displayName="Create object" action="CREATE" businessObject="object"
  -  displayName="Create bucket" action="CREATE" businessObject="bucket"
  -  displayName="Retrieve buckets" action="RETRIEVEALL" businessObject="bucket"
  -  displayName="Delete bucket" action="DELETEALL" businessObject="bucket"
  -  displayName="Retrieve bucket CORS configuration" action="RETRIEVEALL" businessObject="cors"
  -  displayName="Delete bucket CORS configuration" action="DELETEALL" businessObject="cors"
  -  displayName="Update CORS configuration of bucket" action="UPSERT_BUCKET_CORS" businessObject="cors"
  -  displayName="Retrieve bucket ACL" action="RETRIEVEALL" businessObject="bucketacl"
  -  displayName="Update bucket ACL" action="UPDATEALL" businessObject="bucketacl"
  -  displayName="Retrieve object ACL" action="RETRIEVEALL" businessObject="objectacl"
  -  displayName="Update object ACL" action="UPDATEALL" businessObject="objectacl"
  -  displayName="Retrieve object tags" action="RETRIEVEALL" businessObject="objecttags"
  -  displayName="Update object tags" action="UPSERT_OBJECT_TAGS" businessObject="objecttags"
  -  displayName="Delete object tags" action="DELETEALL" businessObject="objecttags"
  -  displayName="Retrieve bucket tags" action="RETRIEVEALL" businessObject="buckettags"
  -  displayName="Update bucket tags" action="UPSERT_BUCKET_TAGS" businessObject="buckettags"
  -  displayName="Delete bucket tags" action="DELETEALL" businessObject="buckettags"
  -  displayName="Retrieve bucket website hosting configuration" action="RETRIEVEALL" businessObject="bucketwebsite"
  -  displayName="Update bucket website hosting configuration" action="UPSERT_BUCKET_WEBSITE" businessObject="bucketwebsite"
  -  displayName="Delete bucket website hosting configuration" action="DELETEALL" businessObject="bucketwebsite"
  -  displayName="Retrieve bucket requester payment configuration" action="RETRIEVEALL" businessObject="bucketrequestpayment"
  -  displayName="Update bucket requester payment configuration" action="UPDATEALL" businessObject="bucketrequestpayment"
  -  displayName="Retrieve bucket default encryption configuration" action="RETRIEVEALL" businessObject="bucketencryption"
  -  displayName="Update bucket default encryption configuration" action="UPSERT_BUCKET_ENCRYPTION" businessObject="bucketencryption"
  -  displayName="Delete bucket default encryption configuration" action="DELETEALL" businessObject="bucketencryption"
  -  displayName="Retrieve bucket lifecycle configuration" action="RETRIEVEALL" businessObject="bucketlifecycleconfiguration"
  -  displayName="Update bucket lifecycle configuration" action="UPSERT_BUCKET_LIFECYCLE_CONFIGURATION" businessObject="bucketlifecycleconfiguration"
  -  displayName="Delete bucket lifecycle configuration" action="DELETEALL" businessObject="bucketlifecycleconfiguration"
  -  displayName="Retrieve bucket policy" action="RETRIEVEALL" businessObject="bucketpolicy"
  -  displayName="Update bucket policy" action="UPSERT_BUCKET_POLICY" businessObject="bucketpolicy"
  -  displayName="Delete bucket policy" action="DELETEALL" businessObject="bucketpolicy"
  -  displayName="Retrieve bucket inventory configuration" action="RETRIEVEALL" businessObject="bucketinventoryconfiguration"
  -  displayName="Update or create bucket inventory configuration" action="UPSERTWITHWHERE" businessObject="bucketinventoryconfiguration"
  -  displayName="Delete bucket inventory configuration" action="DELETEALL" businessObject="bucketinventoryconfiguration"
  -  displayName="Retrieve bucket metrics configuration" action="RETRIEVEALL" businessObject="bucketmetricsconfiguration"
  -  displayName="Update or create bucket metrics configuration" action="UPSERTWITHWHERE" businessObject="bucketmetricsconfiguration"
  -  displayName="Delete bucket metrics configuration" action="DELETEALL" businessObject="bucketmetricsconfiguration"
  -  displayName="Retrieve bucket analytics configuration" action="RETRIEVEALL" businessObject="bucketanalyticsconfiguration"
  -  displayName="Update or create analytics configuration for bucket" action="UPSERTWITHWHERE" businessObject="bucketanalyticsconfiguration"
  -  displayName="Delete bucket analytics configuration" action="DELETEALL" businessObject="bucketanalyticsconfiguration"
  -  displayName="Retrieve bucket replication configuration" action="RETRIEVEALL" businessObject="bucketreplication"
  -  displayName="Update bucket replication configuration" action="UPSERT_BUCKET_REPLICATION" businessObject="bucketreplication"
  -  displayName="Delete bucket replication configuration" action="DELETEALL" businessObject="bucketreplication"
  -  displayName="Retrieve bucket transfer acceleration configuration" action="RETRIEVEALL" businessObject="bucketaccelerateconfiguration"
  -  displayName="Update bucket transfer acceleration configuration" action="UPDATEALL" businessObject="bucketaccelerateconfiguration"
  -  displayName="Retrieve bucket server access logging" action="RETRIEVEALL" businessObject="bucketlogging"
  -  displayName="Update bucket server access logging" action="UPDATEALL" businessObject="bucketlogging"
  -  displayName="Retrieve bucket event configuration" action="RETRIEVEALL" businessObject="bucketnotificationconfiguration"
  -  displayName="Update bucket event configuration" action="UPDATEALL" businessObject="bucketnotificationconfiguration"
  -  displayName="Retrieve object torrent" action="RETRIEVEALL" businessObject="objecttorrent"
  -  displayName="Retrieve object versions" action="RETRIEVEALL" businessObject="objectversioning"
  -  displayName="Update bucket versioning status" action="UPDATEALL" businessObject="bucketversioning"
  -  displayName="Retrieve bucket versioning status" action="RETRIEVEALL" businessObject="bucketversioning"
  -  displayName="Retrieve bucket location" action="RETRIEVEALL" businessObject="bucketlocation"

## Policy Project Requirements

1. Amazon S3 policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "AmazonS3_Request1". Here is an example Amazon S3 policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="AmazonS31" policyTemplate="online_v1_aws_basic_pki" policyType="amazons3" shortDescription="" version="">
        <credentialName>AmazonS3Credential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>AWS_BASIC_PKI</authenticationMethod>
        <roleArn/>
        <region/>
        <hostname/>
        <bucketName/>
        <oidcServerUrl/>
        <profileArn/>
        <trustAnchorArn/>
        <proxyId/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   

