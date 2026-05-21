
## Prerequisite:
Before using this document, you **MUST** first read SKILL.md in the root of the ace-bob skill and follow its workflow and pre-creation validation steps. This document provides connector-specific guidance only and does NOT replace the instructions in SKILL.md.

## Jira node Requirements:
1. Jira Request nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_jira.msgnode and an attribute applicationConnectorType="jira"
2. Jira Input nodes MUST have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_jira.msgnode and an attribute applicationConnectorType="jira"
3. The Jira Request node **MUST** be given a schemaPrefix attribute such as schemaPrefix="gen/MessageFlowName.Jira_Request" where "MessageFlowName" is the name of the message flow and where "Jira_Request" is the type of the message flow node
4. In the ACE Toolkit Application project where the message flow containing the Jira Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.request.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
5. In the ACE Toolkit Application project where the message flow containing the Jira Request node is created, you **MUST** create an empty JSON schema file in the gen subdirectory of the Application project where the message flow is created. The JSON schema file should have a name based on the SchemaPrefix mentioned above. The JSON schema file naming should be like MessageFlowName.NodeName.response.schema.json where "MessageFlowName" is the name of the message flow and where "NodeName" is based upon the type of the message flow node. 
6. The Jira Request node **MUST** be given a policyUrl attribute such as "{DiscoveryConnectorPolicyProject}:Jira1" where "DiscoveryConnectorPolicyProject" is the name of a policy project in the ACE Toolkit workspace and "Jira1" is the name of a .policyxml file in the policy project.
7. For Jira Request nodes only the following combinations of displayName, action and businessObject attributes are allowed:
  -  displayName="Create issue (deprecated)" action="CREATE" businessObject="Issue"
  -  displayName="Retrieve issues (deprecated)" action="RETRIEVEALL" businessObject="Issue"
  -  displayName="Delete issue (deprecated)" action="DELETEALL" businessObject="Issue"
  -  displayName="Update issue (deprecated)" action="UPDATEALL" businessObject="Issue"
  -  displayName="Add subtask to an issue (deprecated)" action="CREATESUBTASK" businessObject="Issue"
  -  displayName="Create issue" action="CREATE" businessObject="IssueV2"
  -  displayName="Retrieve issues" action="RETRIEVEALL" businessObject="IssueV2"
  -  displayName="Delete issue" action="DELETEALL" businessObject="IssueV2"
  -  displayName="Update issue" action="UPDATEALL" businessObject="IssueV2"
  -  displayName="Add subtask to an issue" action="CREATESUBTASK" businessObject="IssueV2"
  -  displayName="Retrieve priorities" action="RETRIEVEALL" businessObject="Priority"
  -  displayName="Retrieve project types" action="RETRIEVEALL" businessObject="ProjectType"
  -  displayName="Retrieve permissions" action="RETRIEVEALL" businessObject="Permissions"
  -  displayName="Retrieve my permissions" action="LISTMYPERMISSIONS" businessObject="Permissions"
  -  displayName="Create project" action="CREATE" businessObject="Project"
  -  displayName="Retrieve projects" action="RETRIEVEALL" businessObject="Project"
  -  displayName="Update project" action="UPDATEALL" businessObject="Project"
  -  displayName="Delete project" action="DELETEALL" businessObject="Project"
  -  displayName="Create filter" action="CREATE" businessObject="Filter"
  -  displayName="Retrieve filters" action="RETRIEVEALL" businessObject="Filter"
  -  displayName="Update filter" action="UPDATEALL" businessObject="Filter"
  -  displayName="Delete filter" action="DELETEALL" businessObject="Filter"
  -  displayName="Retrieve issue links" action="RETRIEVEALL" businessObject="IssueLink"
  -  displayName="Delete issue link" action="DELETEALL" businessObject="IssueLink"
  -  displayName="Retrieve issue link types" action="RETRIEVEALL" businessObject="IssueLinkType"
  -  displayName="Delete issue link type" action="DELETEALL" businessObject="IssueLinkType"
  -  displayName="Update issue link type" action="UPDATEALL" businessObject="IssueLinkType"
  -  displayName="Create issue link type" action="CREATE" businessObject="IssueLinkType"
  -  displayName="Create issue type" action="CREATE" businessObject="IssueType"
  -  displayName="Retrieve issue types" action="RETRIEVEALL" businessObject="IssueType"
  -  displayName="Update issue type" action="UPDATEALL" businessObject="IssueType"
  -  displayName="Delete issue type" action="DELETEALL" businessObject="IssueType"
  -  displayName="Retrieve issue votes" action="RETRIEVEALL" businessObject="IssueVote"
  -  displayName="Add vote to issue" action="ADDISSUEVOTE" businessObject="IssueVote"
  -  displayName="Remove vote from issue" action="REMOVEISSUEVOTE" businessObject="IssueVote"
  -  displayName="Retrieve issue comments" action="RETRIEVEALL" businessObject="IssueComment"
  -  displayName="Delete issue comment" action="DELETEALL" businessObject="IssueComment"
  -  displayName="Update issue comment" action="UPDATEALL" businessObject="IssueComment"
  -  displayName="Create issue comment" action="CREATE" businessObject="IssueComment"
  -  displayName="Create issue attachment" action="CREATE" businessObject="IssueAttachment"
  -  displayName="Retrieve issue attachments" action="RETRIEVEALL" businessObject="IssueAttachment"
  -  displayName="Delete issue  attachment" action="DELETEALL" businessObject="IssueAttachment"
  -  displayName="Download attachment content" action="DOWNLOADATTACHMENTCONTENT" businessObject="IssueAttachment"
  -  displayName="Create issue worklog" action="CREATE" businessObject="IssueWorklog"
  -  displayName="Retrieve issue worklogs" action="RETRIEVEALL" businessObject="IssueWorklog"
  -  displayName="Update issue worklog" action="UPDATEALL" businessObject="IssueWorklog"
  -  displayName="Delete issue worklog" action="DELETEALL" businessObject="IssueWorklog"
  -  displayName="Retrieve project versions" action="RETRIEVEALL" businessObject="ProjectVersion"
  -  displayName="Delete project version" action="DELETEALL" businessObject="ProjectVersion"
  -  displayName="Update project version" action="UPDATEALL" businessObject="ProjectVersion"
  -  displayName="Create project version" action="CREATE" businessObject="ProjectVersion"
  -  displayName="Retrieve project components" action="RETRIEVEALL" businessObject="ProjectComponent"
  -  displayName="Delete project component" action="DELETEALL" businessObject="ProjectComponent"
  -  displayName="Create project component" action="CREATE" businessObject="ProjectComponent"
  -  displayName="Update project component" action="UPDATEALL" businessObject="ProjectComponent"
  -  displayName="Retrieve notification schemes" action="RETRIEVEALL" businessObject="NotificationScheme"
  -  displayName="Retrieve resolutions" action="RETRIEVEALL" businessObject="Resolution"
  -  displayName="Retrieve statuses" action="RETRIEVEALL" businessObject="Status"
  -  displayName="Retrieve project roles" action="RETRIEVEALL" businessObject="ProjectRole"
  -  displayName="Delete project role" action="DELETEALL" businessObject="ProjectRole"
  -  displayName="Update project role" action="UPDATEALL" businessObject="ProjectRole"
  -  displayName="Create project role" action="CREATE" businessObject="ProjectRole"
  -  displayName="Retrieve groups" action="RETRIEVEALL" businessObject="Group"
  -  displayName="Delete group" action="DELETEALL" businessObject="Group"
  -  displayName="Create group" action="CREATE" businessObject="Group"
  -  displayName="Retrieve users" action="RETRIEVEALL" businessObject="User"
  -  displayName="Retrieve users assignable for issue" action="USERASSIGNABLEFORISSUE" businessObject="User"
  -  displayName="Retrieve users assignable for project" action="USERASSIGNABLEFORPROJECT" businessObject="User"
  -  displayName="Find users with permissions" action="USERSWITHPERMISSIONS" businessObject="User"
  -  displayName="Retrieve groups" action="RETRIEVEALL" businessObject="GroupCollection"
  -  displayName="Retrieve issues" action="RETRIEVEALL" businessObject="IssueCollection"
  -  displayName="Retrieve all issues" action="RETRIEVEALL" businessObject="Issue collections"
  -  displayName="Retrieve issue watchers" action="RETRIEVEALL" businessObject="IssueWatcher"
  -  displayName="Add me as watcher to issue" action="ADDISSUEWATCHER" businessObject="IssueWatcher"
  -  displayName="Remove from issue watcher list" action="REMOVEISSUEWATCHER" businessObject="IssueWatcher"
  -  displayName="Retrieve issue comments" action="RETRIEVEALL" businessObject="IssueCommentCollection"
  
## Policy Project Requirements

1. Jira policies MUST be created in a separate Policy Project, NOT in the Application project
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
8. Policy files should be placed in the root of the Policy Project. If the user does not indicate which policy to use you **MUST** create one for the user in the policy project. A good name can be derived from the type of the node followed by a number (starting from 1) such as for example "Jira_Request1". Here is an example Jira policy:
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <policies>
     <policy longDescription="" policyName="Jira1" policyTemplate="online_v1_basic" policyType="jira" shortDescription="" version="">
        <credentialName>JiraCredential</credentialName>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <endpointUrl>https://myjirahost:port</endpointUrl>
        <proxyId/>
     </policy>
   </policies>
   ```  
9. When creating a policy file (which has an extension .policyxml) you **MUST** validate the structure and contents of the policy file using the XML schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\Policy\\Policy.xsd   

