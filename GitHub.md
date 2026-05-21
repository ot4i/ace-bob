
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## GitHub node Requirements:
1. GitHub Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_github.msgnode and an attribute applicationConnectorType="github"
2. GitHub Input nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_github.msgnode and an attribute applicationConnectorType="github"
3. The GitHub Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.GitHub_Request" where "MessageFlowName" is the name of the message flow and where "GitHub_Request" is the type of the message flow node
4. In the ACE Toolkit Application project where the message flow containing the GitHub Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. In the ACE Toolkit Application project where the message flow containing the GitHub Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
6. The GitHub Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:GitHub1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "GitHub1" is the name of a .policyxml file in the policy project.
7. For GitHub Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Retrieve organizations" action="RETRIEVEALL" businessObject="Organization"
  -  displayName="Update organization" action="UPDATEALL" businessObject="Organization"
  -  displayName="Create repository" action="CREATE" businessObject="Repository"
  -  displayName="Retrieve repositories" action="RETRIEVEALL" businessObject="Repository"
  -  displayName="Update repository" action="UPDATEALL" businessObject="Repository"
  -  displayName="Delete repository" action="DELETEALL" businessObject="Repository"
  -  displayName="Create issue" action="CREATE" businessObject="Issue"
  -  displayName="Retrieve issues" action="RETRIEVEALL" businessObject="Issue"
  -  displayName="Update issue" action="UPDATEALL" businessObject="Issue"
  -  displayName="Add assignees" action="ADDASSIGNEES" businessObject="Issue"
  -  displayName="Remove assignees" action="REMOVEASSIGNEES" businessObject="Issue"
  -  displayName="Create comment" action="CREATE" businessObject="Comment"
  -  displayName="Retrieve comments" action="RETRIEVEALL" businessObject="Comment"
  -  displayName="Update comment" action="UPDATEALL" businessObject="Comment"
  -  displayName="Delete comment" action="DELETEALL" businessObject="Comment"
  -  displayName="Create pull request" action="CREATE" businessObject="Pullrequest"
  -  displayName="Retrieve pull requests" action="RETRIEVEALL" businessObject="Pullrequest"
  -  displayName="Update pull request" action="UPDATEALL" businessObject="Pullrequest"
  -  displayName="Merge pull request" action="MERGEPULLREQUEST" businessObject="Pullrequest"
  -  displayName="Create review comment" action="CREATE" businessObject="Reviewcomment"
  -  displayName="Retrieve review comments" action="RETRIEVEALL" businessObject="Reviewcomment"
  -  displayName="Update review comment" action="UPDATEALL" businessObject="Reviewcomment"
  -  displayName="Delete review comment" action="DELETEALL" businessObject="Reviewcomment"
  -  displayName="Reply review comment" action="REPLYREVIEWCOMMENT" businessObject="Reviewcomment"
  -  displayName="Create review" action="CREATE" businessObject="Review"
  -  displayName="Retrieve reviews" action="RETRIEVEALL" businessObject="Review"
  -  displayName="Update review" action="UPDATEALL" businessObject="Review"
  -  displayName="Delete review" action="DELETEALL" businessObject="Review"
  -  displayName="Submit review" action="SUBMITREVIEW" businessObject="Review"
  -  displayName="Request review" action="REQUESTREVIEWERS" businessObject="Reviewrequest"
  -  displayName="Retrieve branches" action="RETRIEVEALL" businessObject="Branch"
  -  displayName="Merge branch" action="MERGEBRANCH" businessObject="Branch"
  -  displayName="Retrieve commits" action="RETRIEVEALL" businessObject="Commit"
  -  displayName="Create commit comment" action="CREATE" businessObject="Commitcomment"
  -  displayName="Retrieve commit comments" action="RETRIEVEALL" businessObject="Commitcomment"
  -  displayName="Update commit comment" action="UPDATEALL" businessObject="Commitcomment"
  -  displayName="Delete commit comment" action="DELETEALL" businessObject="Commitcomment"
  -  displayName="Create team" action="CREATE" businessObject="Team"
  -  displayName="Retrieve teams" action="RETRIEVEALL" businessObject="Team"
  -  displayName="Update team" action="UPDATEALL" businessObject="Team"
  -  displayName="Delete team" action="DELETEALL" businessObject="Team"
  -  displayName="Add or update team member" action="ADDUPDATEMEMBERSHIP" businessObject="Team"
  -  displayName="Remove team member" action="REMOVEMEMBERSHIP" businessObject="Team"
  -  displayName="Retrieve users" action="RETRIEVEALL" businessObject="User"
  -  displayName="Retrieve collaborators" action="RETRIEVEALL" businessObject="Collaborator"
  
## Policy Project Requirements

1. GitHub policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "GitHub_Request1". Here is an example GitHub policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="GitHub1" policyTemplate="online_v1_basic" policyType="github" shortDescription="" version="">
        <credentialName>GitHubCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl/>
        <proxyId/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   
