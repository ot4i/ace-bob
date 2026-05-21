
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Redis node Requirements:
1. Redis Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_rediscache.msgnode and an attribute applicationConnectorType="rediscache"
2. The Redis Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.Redis_Request" where "MessageFlowName" is the name of the message flow and where "Redis_Request" is the type of the message flow node
3. In the ACE Toolkit Application project where the message flow containing the Redis Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
4. In the ACE Toolkit Application project where the message flow containing the Redis Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. The Redis Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:Redis1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "Redis1" is the name of a .policyxml file in the policy project.
6. For Redis Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Delete key" action="DELETEALL" businessObject="Key"
  -  displayName="Retrieve keys" action="RETRIEVEKEYS" businessObject="Key"
  -  displayName="Check key presence" action="CHECKKEYPRESENCE" businessObject="Key"
  -  displayName="Get data type of key" action="GETDATATYPEOFKEY" businessObject="Key"
  -  displayName="Set expire timeout (seconds/milliseconds)" action="SETEXPIRETIMEOUT" businessObject="Key"
  -  displayName="Set expire at time" action="SETEXPIREATTIME" businessObject="Key"
  -  displayName="Get time to live" action="GETTIMETOLIVE" businessObject="Key"
  -  displayName="Remove expire timeout on key" action="REMOVEEXPIRETIMEOUTONKEY" businessObject="Key"
  -  displayName="Rename key" action="RENAMEKEY" businessObject="Key"
  -  displayName="Update or create string" action="UPSERTWITHWHERE" businessObject="String"
  -  displayName="Append a value to string" action="APPENDVALUETOSTRING" businessObject="String"
  -  displayName="Get value" action="GETVALUE" businessObject="String"
  -  displayName="Update or create hash" action="UPSERTWITHWHERE" businessObject="Hash"
  -  displayName="Delete hash field" action="DELETEALL" businessObject="Hash"
  -  displayName="Check hash field presence" action="CHECKFIELDPRESENCE" businessObject="Hash"
  -  displayName="Get hash field count" action="GETFIELDCOUNT" businessObject="Hash"
  -  displayName="Get hash field value" action="GETFIELDVALUE" businessObject="Hash"
  -  displayName="Update or create set" action="UPSERTWITHWHERE" businessObject="Set"
  -  displayName="Delete set member" action="DELETEALL" businessObject="Set"
  -  displayName="Check set member presence" action="CHECKMEMBERPRESENCE" businessObject="Set"
  -  displayName="Get set member count" action="GETMEMBERCOUNT" businessObject="Set"
  -  displayName="Retrieve set members" action="RETRIEVEALLMEMBERS" businessObject="Set"
  -  displayName="Update or create list" action="UPSERTWITHWHERE" businessObject="List"
  -  displayName="Update list" action="UPDATEALL" businessObject="List"
  -  displayName="Delete list element" action="DELETEALL" businessObject="List"
  -  displayName="Get list length" action="GETLISTLENGTH" businessObject="List"
  -  displayName="Trim the list" action="TRIMTHELIST" businessObject="List"
  -  displayName="Retrieve list elements" action="RETRIEVEELEMENT" businessObject="List"
  -  displayName="Update or create sorted set" action="UPSERTWITHWHERE" businessObject="SortedSet"
  -  displayName="Delete sorted set member" action="DELETEALL" businessObject="SortedSet"
  -  displayName="Get sorted set member count" action="GETSORTEDSETMEMBERCOUNT" businessObject="SortedSet"
  -  displayName="Get member count by score range" action="GETMEMBERCOUNTBYSCORERANGE" businessObject="SortedSet"
  -  displayName="Get sorted set member rank" action="GETMEMBERRANK" businessObject="SortedSet"
  -  displayName="Get sorted set member score" action="GETMEMBERSCORE" businessObject="SortedSet"
  -  displayName="Retrieve sorted set members" action="RETRIEVEMEMBER" businessObject="SortedSet"

## Policy Project Requirements

1. Redis policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "Redis_Request1". Here is an example Redis policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="Redis1" policyTemplate="RedisConnection" policyType="RedisConnection" shortDescription="" version="">
        <hostname>localhost</hostname>
        <port>6379</port>
        <databaseNumber>0</databaseNumber>
        <clientName/>
        <securityIdentity>RedisCredential</securityIdentity>
        <useSSL>false</useSSL>
        <sslProtocol>TLSv1.3</sslProtocol>
        <sslRejectUnauthorized>true</sslRejectUnauthorized>
        <maximumConnectionCount>8</maximumConnectionCount>
        <maximumIdleConnectionCount>8</maximumIdleConnectionCount>
        <maximumIdleConnectionAge>60</maximumIdleConnectionAge>
        <connectionTimeoutSecs>2</connectionTimeoutSecs>
        <commandTimeoutSecs>120</commandTimeoutSecs>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   

