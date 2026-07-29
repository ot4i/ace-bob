---
name: ace-bob
description: Create IBM App Connect Enterprise message flows and associated configuration files such as ESQL, Java and Maps
---

# ACE Toolkit Message Flow Generator
You are an expert at developing integration artifacts of various types for IBM App Connect Enterprise (ACE). Specifically you are trained for:
- Creating message flows (files with filename "*.msgflow)
- Creating ESQL for message flow Compute nodes (files with filename "*.esql")
- Creating Java for message flow JavaCompute nodes (files with filename "*.java")
- Creating Maps for message flow Map nodes (files with filename "*.map")
- Providing a summary for each task you complete.

#️ **CRITICAL: Pre-Creation Validation**
Before creating **ANY** artifacts, you **MUST**:
- Read the **ENTIRE** relevant section for the node/project type
- Verify the **EXACT** xmi:type namespace prefix from this document. DO NOT copy them from example .msgflow files as they may contain outdated or incorrect values.
- Verify the **EXACT** project natures required
- DO **NOT** copy from example files - they may be outdated 

# Workflow
1. **Create an ACE Toolkit Application Project**
   - If the user did not mention an existing Application project, you should create one. 
   - The ACE Toolkit Application Project provides a location where output files such as *.msgflow, *.esql, *.msp will be created.
   - When generating .msgflow files or .esql files they should always be created inside an ACE Toolkit Application project.
   - If you have not been given a name for the ACE Toolkit Application project, use the same name as the message flow (without the .msgflow file extension)
   - An ACE Toolkit Application project is a specialized form of an Eclipse project

2. **Create the .project file**
   - If you created a new ACE Toolkit Application Project it **MUST** contain a .project file.
   - To be recognised as an Eclipse project, the file system directory representing the project **MUST** contain a .project file
   - ACE Toolkit Application projects **MUST** contain the following project natures section in the .project file:
     ```
	 <natures>
		<nature>com.ibm.etools.msgbroker.tooling.applicationNature</nature>
		<nature>com.ibm.etools.msgbroker.tooling.messageBrokerProjectNature</nature>
	 </natures>
	 ```
   - ACE Toolkit Application projects **MUST** contain the following buildSpec section in the .project file:
     ```
     <buildSpec>
		<buildCommand>
			<name>com.ibm.etools.mft.applib.applibbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.applib.applibresourcevalidator</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.connector.policy.ui.PolicyBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.applib.mbprojectbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.msg.validation.dfdl.mlibdfdlbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.flow.adapters.adapterbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.flow.sca.scabuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.msg.validation.dfdl.mbprojectresourcesbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.esql.lang.esqllangbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.map.builder.mslmappingbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.flow.msgflowxsltbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.flow.msgflowbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.decision.service.ui.decisionservicerulebuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.pattern.capture.PatternBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.json.builder.JSONBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.restapi.ui.restApiDefinitionsBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.policy.ui.policybuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.msg.assembly.messageAssemblyBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.msg.validation.dfdl.dfdlqnamevalidator</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.bar.ext.barbuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.unittest.ui.TestCaseBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
	 </buildSpec>
	 ```   
3. **Create the .settings subdirectory in the project**
   - If you created a new ACE Toolkit Application Project it **MUST** contain a .settings subdirectory
   - The .settings folder **MUST** contain a file named org.eclipse.core.resources.prefs which should contain the following:
     ```
     eclipse.preferences.version=1
     encoding/<project>=UTF-8
     ```

4. **Create the application.descriptor file in the project**
   - If you created a new ACE Toolkit Application Project it **MUST** contain an application.descriptor file in the root of the project directory
   - The Application descriptor file has a fixed name application.descriptor. The content of the application.descriptor looks like this:
     ```
     <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
     <ns2:appDescriptor xmlns="http://com.ibm.etools.mft.descriptor.base" xmlns:ns2="http://com.ibm.etools.mft.descriptor.app">
       <references/> 
     </ns2:appDescriptor>
     ```
   - If you created a new ACE Toolkit Application Project, then at the very end of your task (after you have completed the rest of the steps defined below) you **MUST** always print the following message back to the IBM Bob user (which helps guide the user on next steps) at the very end of your processing: "If you are working in the ACE Toolkit then to see the results and do further work with the generated project in the Application Development view, use the menu option to File > Import > Existing Projects into Workspace."	 
	 
5. **Create a message flow** 
   - When asked to create a message flow, you will create a *.msgflow file which will be understood by ACE Toolkit (do not get confused with creating a yaml file for ACE Designer)
   - Before adding any node, you **MUST** verify its xmi:type namespace prefix in the list below
   - When adding a node to a message flow, the xml element called nodes inside the message flow file **MUST** have an xmi:type attribute
   - When adding a node to a message flow, the namespace prefix used in the value of the xmi:type attribute indicates the type of the node. This value **MUST** be validated by checking the schema file at C:\\Program Files\\IBM\\ACE\\13.0.7.0\\common\\schemas\\MessageFlow\\MessageFlow.xsd and within that file finding an element with a name attribute that matches.
   - If you add a Subflow Input node to a message flow, it **MUST** have an xmi:type="eflow:FCMSource"
   - If you add a Subflow Output node to a message flow, it **MUST** have an xmi:type="eflow:FCMSink"
   - If you add a Callable Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCallableFlowInput.msgnode
   - If you add a Callable Reply node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCallableFlowReply.msgnode
   - If you add a Callable Flow Invoke node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCallableFlowInvoke.msgnode
   - If you add a Callable Flow Async Invoke node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCallableFlowAsyncInvoke.msgnode
   - If you add a Callable Flow Async Response node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCallableFlowAsyncResponse.msgnode
   - If you add a Throw node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmThrow.msgnode
   - If you add a Try Catch node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTryCatch.msgnode
   - If you add a Trace node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTrace.msgnode
   - If you add a Validate node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmValidate.msgnode
   - If you add a Log node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmLog.msgnode
   - If you add a Aggregate Control node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmAggregateControl.msgnode
   - If you add a Aggregate Reply node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmAggregateReply.msgnode
   - If you add a Aggregate Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmAggregateRequest.msgnode
   - If you add a Collector node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCollector.msgnode
   - If you add a Group Scatter node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmGroupScatter.msgnode
   - If you add a Group Gather node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmGroupGather.msgnode
   - If you add a Group Complete node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmGroupComplete.msgnode
   - If you add a Filter node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFilter.msgnode
   - If you add a Label node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmLabel.msgnode
   - If you add a Route To Label node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmRouteToLabel.msgnode
   - If you add a Route node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmRoute.msgnode
   - If you add a Flow Order node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFlowOrder.msgnode
   - If you add a Resequence node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmReSequence.msgnode
   - If you add a Sequence node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSequence.msgnode
   - If you add a Pass through node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmPassthru.msgnode
   - If you add a Security PEP node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSecurityPEP.msgnode
   - If you add a Timeout Control node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTimeoutControl.msgnode
   - If you add a Timeout Notification node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTimeoutNotification.msgnode
   - If you add a Scheduler node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmScheduler.msgnode
   - If you add a JSONata Mapping node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJSONataMapping.msgnode
   - If you add a .NET Compute node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmDotNetCompute.msgnode
   - If you add a Mapping node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmMSLMapping.msgnode
   - If you add a XSL Transform node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmXslMqsi.msgnode
   - If you add a Compute node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCompute.msgnode
   - If you add a Java Compute node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJavaCompute.msgnode
   - If you add a Reset Content Descriptor node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmResetContentDescriptor.msgnode 
   - If you add a Amazon CloudWatch Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazoncloudwatch.msgnode and an attribute applicationConnectorType="amazoncloudwatch"
   - If you add a Amazon DynamoDB Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazondynamodb.msgnode and an attribute applicationConnectorType="amazondynamodb"
   - If you add a Amazon EC2 Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazonec2.msgnode and an attribute applicationConnectorType="amazonec2"
   - If you add a Amazon EventBridge Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazoneventbridge.msgnode and an attribute applicationConnectorType="amazoneventbridge"
   - If you add a Amazon EventBridge Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_amazoneventbridge.msgnode and an attribute applicationConnectorType="amazoneventbridge"
   - If you add a Amazon Kinesis Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazonkinesis.msgnode and an attribute applicationConnectorType="amazonkinesis"
   - If you add a Amazon RDS Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazonrds.msgnode and an attribute applicationConnectorType="amazonrds"
   - If you add a Amazon S3 Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazons3.msgnode and an attribute applicationConnectorType="amazons3"
   - If you add a Amazon S3 Request node to a message flow you **MUST** read the skill guidance in AmazonS3.md to help determine the node properties	 
   - If you add a Amazon SES Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazonses.msgnode and an attribute applicationConnectorType="amazonses"
   - If you add a Amazon SNS Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazonsns.msgnode and an attribute applicationConnectorType="amazonsns"
   - If you add a Amazon SQS Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazonsqs.msgnode and an attribute applicationConnectorType="amazonsqs"
   - If you add a Anaplan Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_anaplan.msgnode and an attribute applicationConnectorType="anaplan"
   - If you add a Apache Pulsar Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_apachepulsar.msgnode and an attribute applicationConnectorType="apachepulsar"
   - If you add a Apache Pulsar Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_apachepulsar.msgnode and an attribute applicationConnectorType="apachepulsar"
   - If you add a Amazon SQS Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_amazonsqs.msgnode and an attribute applicationConnectorType="amazonsqs"
   - If you add a Asana Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_asana.msgnode and an attribute applicationConnectorType="asana"
   - If you add a Asana Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_asana.msgnode and an attribute applicationConnectorType="asana"
   - If you add a Astra DB Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_astradb.msgnode and an attribute applicationConnectorType="astradb"
   - If you add a Astra DB Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_astradb.msgnode and an attribute applicationConnectorType="astradb"
   - If you add a AWS Lambda Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_amazonlambda.msgnode and an attribute applicationConnectorType="amazonlambda"
   - If you add a BambooHR Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_bamboohr.msgnode and an attribute applicationConnectorType="bamboohr"
   - If you add a Box Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_box.msgnode and an attribute applicationConnectorType="box"
   - If you add a Box Request node to a message flow you **MUST** read the skill guidance in Box.md to help determine the node properties
   - If you add a Businessmap Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_businessmap.msgnode and an attribute applicationConnectorType="businessmap"
   - If you add a Businessmap Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_businessmap.msgnode and an attribute applicationConnectorType="businessmap"
   - If you add a Calendly Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_calendly.msgnode and an attribute applicationConnectorType="calendly"
   - If you add a ClickSend Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_clicksend.msgnode and an attribute applicationConnectorType="clicksend"
   - If you add a ClickSend Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_clicksend.msgnode and an attribute applicationConnectorType="clicksend"
   - If you add a CMIS Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_cmis.msgnode and an attribute applicationConnectorType="cmis"
   - If you add a CMIS Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_cmis.msgnode and an attribute applicationConnectorType="cmis"
   - If you add a Confluence Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_confluence.msgnode and an attribute applicationConnectorType="confluence"
   - If you add a Couchbase Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_couchbase.msgnode and an attribute applicationConnectorType="couchbase"
   - If you add a Coupa Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_coupa.msgnode and an attribute applicationConnectorType="coupa"
   - If you add a Coupa Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_coupa.msgnode and an attribute applicationConnectorType="coupa"
   - If you add a Crystal Ball Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_crystalball.msgnode and an attribute applicationConnectorType="crystalball"
   - If you add a CORBA Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCORBARequest.msgnode
   - If you add a Database Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmDatabaseInput.msgnode
   - If you add a Database node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmDatabase.msgnode
   - If you add a Database Retrieve node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmDatabaseRetrieve.msgnode
   - If you add a Database Route node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmDatabaseRoute.msgnode
   - If you add a Change Data Capture node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmChangeDataCapture.msgnode
   - If you add a Databricks Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_databricks.msgnode and an attribute applicationConnectorType="databricks"
   - If you add a DocuSign Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_docusign.msgnode and an attribute applicationConnectorType="docusign"
   - If you add a Dropbox Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_dropbox.msgnode and an attribute applicationConnectorType="dropbox"
   - If you add a Dropbox Request node to a message flow you **MUST** read the skill guidance in Dropbox.md to help determine the node properties
   - If you add a Email Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmEmailOutput.msgnode
   - If you add a Email Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmEmailInput.msgnode
   - If you add a Eventbrite Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_eventbrite.msgnode and an attribute applicationConnectorType="eventbrite"
   - If you add a Eventbrite Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_eventbrite.msgnode and an attribute applicationConnectorType="eventbrite"
   - If you add a Factorial HR Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_factorialhr.msgnode and an attribute applicationConnectorType="factorialhr"
   - If you add a Expensify Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_expensify.msgnode and an attribute applicationConnectorType="expensify"
   - If you add a File Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix ofomIbmFileInput.msgnode
   - If you add a File Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFileOutput.msgnode
   - If you add a File Read node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFileRead.msgnode
   - If you add a File Exists node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFileExists.msgnode
   - If you add a File Iterator node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFileIterator.msgnode
   - If you add a Freshservice Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_freshservice.msgnode and an attribute applicationConnectorType="freshservice"
   - If you add a Freshservice Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_freshservice.msgnode and an attribute applicationConnectorType="freshservice"
   - If you add a Front Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_front.msgnode and an attribute applicationConnectorType="front"
   - If you add a Front Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_front.msgnode and an attribute applicationConnectorType="front"
   - If you add a GitHub Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_github.msgnode and an attribute applicationConnectorType="github"
   - If you add a GitHub Request node to a message flow you **MUST** read the skill guidance in GitHub.md to help determine the node properties	 
   - If you add a GitHub Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_github.msgnode and an attribute applicationConnectorType="github"
   - If you add a GitHub Input node to a message flow you **MUST** read the skill guidance in GitHub.md to help determine the node properties
   - If you add a GitLab Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_gitlab.msgnode and an attribute applicationConnectorType="gitlab"
   - If you add a GitLab Request node to a message flow you **MUST** read the skill guidance in GitLab.md to help determine the node properties	 
   - If you add a GitLab Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_gitlab.msgnode and an attribute applicationConnectorType="gitlab"
   - If you add a GitLab Input node to a message flow you **MUST** read the skill guidance in GitLab.md to help determine the node properties
   - If you add a Gmail Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_gmail.msgnode and an attribute applicationConnectorType="gmail"
   - If you add a Gmail Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_gmail.msgnode and an attribute applicationConnectorType="gmail"
   - If you add a Google Analytics Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googleanalytics4.msgnode and an attribute applicationConnectorType="googleanalytics4"
   - If you add a Google Calendar Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_googlecalendar.msgnode and an attribute applicationConnectorType="googlecalendar"
   - If you add a Google Calendar Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlecalendar.msgnode and an attribute applicationConnectorType="googlecalendar"
   - If you add a Google Chat Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlechat.msgnode and an attribute applicationConnectorType="googlechat"
   - If you add a Google Cloud BigQuery Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlebigquery.msgnode and an attribute applicationConnectorType="googlebigquery"
   - If you add a Google Cloud PubSub Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_googlepubsub.msgnode and an attribute applicationConnectorType="googlepubsub"
   - If you add a Google Cloud PubSub Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlepubsub.msgnode and an attribute applicationConnectorType="googlepubsub"
   - If you add a Google Cloud Storage Request node to a message flow read the skill guidance in GitLab.md to help determine the node properties   
   - If you add a Google Cloud Storage Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlecloudstorage.msgnode and an attribute applicationConnectorType="googlecloudstorage"
   - If you add a Google Cloud Storage Request node to a message flow you **MUST** read the skill guidance in GoogleCloudStorage.md to help determine the node properties      
   - If you add a Google Contacts Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlecontacts.msgnode and an attribute applicationConnectorType="googlecontacts"
   - If you add a Google Drive Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googledrive.msgnode and an attribute applicationConnectorType="googledrive"
   - If you add a Google Gemini Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlegemini.msgnode and an attribute applicationConnectorType="googlegemini"
   - If you add a Google Groups Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlegroups.msgnode and an attribute applicationConnectorType="googlegroups"
   - If you add a Google Sheets Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_googlesheet.msgnode and an attribute applicationConnectorType="googlesheet"
   - If you add a Google Sheets Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googlesheet.msgnode and an attribute applicationConnectorType="googlesheet"
   - If you add a Google Tasks Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googletasks.msgnode and an attribute applicationConnectorType="googletasks"
   - If you add a Google Translate Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googletranslate.msgnode and an attribute applicationConnectorType="googletranslate"
   - If you add a Google Universal Analytics Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_googleanalytics.msgnode and an attribute applicationConnectorType="googleanalytics"
   - If you add a Greenhouse Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_greenhouse.msgnode and an attribute applicationConnectorType="greenhouse"
   - If you add a Greenhouse Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_greenhouse.msgnode and an attribute applicationConnectorType="greenhouse"
   - If you add a HTTP Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmWSInput.msgnode
   - If you add a HTTP Reply node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmWSReply.msgnode
   - If you add a HTTP Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmWSRequest.msgnode
   - If you add a HTTP Header node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmHTTPHeader.msgnode
   - If you add a HTTP Async Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmHTTPAsyncRequest.msgnode
   - If you add a HTTP Async Response node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmHTTPAsyncResponse.msgnode
   - If you add a HubSpot CRM Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_hubspotcrm.msgnode and an attribute  applicationConnectorType="hubspotcrm"
   - If you add a HubSpot Marketing Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_hubspotmarketing.msgnode and an attribute  applicationConnectorType="hubspotmarketing"
   - If you add a HubSpot Marketing Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_hubspotmarketing.msgnode:FCMComposite_1" xmi:id="FCMComposite_1_3" location="128,74" applicationConnectorType="hubspotmarketing"
   - If you add a Hunter Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_hunter.msgnode and an attribute applicationConnectorType="hunter"
   - If you add a IBM Aspera Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ibmaspera.msgnode and an attribute applicationConnectorType="ibmaspera"
   - If you add a CICS Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCICSIPICRequest.msgnode
   - If you add a IBM Cloud Object Storage S3 Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ibmcoss3.msgnode and an attribute applicationConnectorType="ibmcoss3"
   - If you add a IBM Cloudant Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_cloudantdb.msgnode and an attribute applicationConnectorType="cloudantdb"
   - If you add a IBM Cloudant Request node to a message flow you **MUST** read the skill guidance in IBMCloudant.md to help determine the node properties      
   - If you add a IBM Engineering Workflow Management Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_ibmewm.msgnode and an attribute applicationConnectorType="ibmewm"
   - If you add a IBM Engineering Workflow Management Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ibmewm.msgnode and an attribute applicationConnectorType="ibmewm"
   - If you add a IBM FileNet Content Manager Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_filenet.msgnode and an attribute applicationConnectorType="filenet"
   - If you add a IBM Food Trust Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ift.msgnode and an attribute  applicationConnectorType="ift"
   - If you add a IMS Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmIMSRequest.msgnode
   - If you add a IBM Maximo Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_maximo.msgnode and an attribute applicationConnectorType="maximo"
   - If you add a IBM Maximo Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_maximo.msgnode and an attribute applicationConnectorType="maximo"
   - If you add a MQ Input node to a message flow
     - It **MUST** have an xmi:type attribute using the namespace prefix of ComIbmMQInput.msgnode
	 - It **MUST** have a queueName attribute. If not expressed, you **MUST** ask the user for their preference.
   - If you add a MQ Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmMQOutput.msgnode
   - If you add a MQ Reply node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmMQReply.msgnode
   - If you add a MQ Get node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmMQGet.msgnode
   - If you add a MQ Header node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmMQHeader.msgnode
   - If you add a Publication node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmPublication.msgnode
   - If you add a FTE Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFTEInput.msgnode
   - If you add a FTE Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmFTEOutput.msgnode
   - If you add a ODM Rules node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmODMRules.msgnode
   - If you add a IBM OpenPages with Watson Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_ibmopenpages.msgnode and an attribute applicationConnectorType="ibmopenpages"
   - If you add a IBM OpenPages with Watson Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ibmopenpages.msgnode and an attribute applicationConnectorType="ibmopenpages"
   - If you add a IBM Planning Analytics Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_planninganalytics.msgnode and an attribute applicationConnectorType="planninganalytics"
   - If you add a CD Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCDInput.msgnode
   - If you add a CD Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmCDOutput.msgnode
   - If you add a IBM Sterling Intelligent Promising Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ibmsterlingiv.msgnode and an attribute applicationConnectorType="ibmsterlingiv"
   - If you add a IBM Targetprocess Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_apptiotargetprocess.msgnode and an attribute applicationConnectorType="apptiotargetprocess"
   - If you add a IBM Targetprocess Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_apptiotargetprocess.msgnode and an attribute applicationConnectorType="apptiotargetprocess"
   - If you add a IBM Watson Discovery Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_watsondiscovery.msgnode and an attribute applicationConnectorType="watsondiscovery"
   - If you add a IBM watsonx.ai Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ibmwatsonxai.msgnode and an attribute applicationConnectorType="ibmwatsonxai"
   - If you add a IBM zOS Connect Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_zosconnect.msgnode and an attribute applicationConnectorType="zosconnect"
   - If you add a Infobip Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_infobip.msgnode and an attribute applicationConnectorType="infobip"
   - If you add a Insightly Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_insightly.msgnode and an attribute applicationConnectorType="insightly"
   - If you add a Insightly Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_insightly.msgnode and an attribute applicationConnectorType="insightly"
   - If you add a Jenkins Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_jenkins.msgnode and an attribute applicationConnectorType="jenkins"
   - If you add a Jenkins Request node to a message flow you **MUST** read the skill guidance in Jenkins.md to help determine the node properties   
   - If you add a Jira Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_jira.msgnode and an attribute applicationConnectorType="jira"
   - If you add a Jira Request node to a message flow you **MUST** read the skill guidance in Jira.md to help determine the node properties
   - If you add a Jira Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_jira.msgnode and an attribute applicationConnectorType="jira"
   - If you add a Jira Input node to a message flow you **MUST** read the skill guidance in Jira.md to help determine the node properties
   - If you add a JMS Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJMSClientInput.msgnode
   - If you add a JMS Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJMSClientOutput.msgnode
   - If you add a JMS Reply node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJMSClientReply.msgnode
   - If you add a JMS Receive node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJMSClientReceive.msgnode
   - If you add a JMS Header node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJMSHeader.msgnode
   - If you add a Kafka Consumer node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmKafkaMsgConsumer.msgnode
   - If you add a Kafka Producer node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmKafkaMsgProducer.msgnode
   - If you add a Kafka Read node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmKafkaMsgRead.msgnode
   - If you add a LDAP Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_ldap.msgnode and an attribute applicationConnectorType="ldap"
   - If you add a LDAP Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ldap.msgnode and an attribute applicationConnectorType="ldap"
   - If you add a Loop Back Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of com_ibm_connector_loopback_ComIbmRequest.msgnode and an attribute connectorName="iib-loopback-connector"
   - If you add a Magento Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_magento.msgnode and an attribute applicationConnectorType="magento"
   - If you add a Magento Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_magento.msgnode and an attribute applicationConnectorType="magento"
   - If you add a Mailchimp Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_mailchimp.msgnode and an attribute applicationConnectorType="mailchimp"
   - If you add a Mailchimp Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_mailchimp.msgnode and an attribute applicationConnectorType="mailchimp"
   - If you add a Marketo Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_marketo.msgnode and an attribute applicationConnectorType="marketo"
   - If you add a Marketo Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_marketo.msgnode and an attribute applicationConnectorType="marketo"
   - If you add a Microsoft Active Directory Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_msad.msgnode and an attribute applicationConnectorType="msad"
   - If you add a Microsoft Active Directory Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msad.msgnode and an attribute applicationConnectorType="msad"
   - If you add a Microsoft Azure Blob storage Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azureblobstorage.msgnode and an attribute applicationConnectorType="azureblobstorage"
   - If you add a Microsoft Azure Blob storage Request node to a message flow you **MUST** read the skill guidance in MicrosoftAzureBlobstorage.md to help determine the node properties
   - If you add a Microsoft Azure Cosmos DB Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azurecosmosdb.msgnode and an attribute applicationConnectorType="azurecosmosdb"
   - If you add a Microsoft Azure DevOps Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_azuredevops.msgnode and an attribute applicationConnectorType="azuredevops"
   - If you add a Microsoft Azure DevOps Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azuredevops.msgnode and an attribute applicationConnectorType="azuredevops"
   - If you add a Microsoft Azure Event Hubs Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_azureeventhub.msgnode and an attribute applicationConnectorType="azureeventhub"
   - If you add a Microsoft Azure Event Hubs Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azureeventhub.msgnode and an attribute applicationConnectorType="azureeventhub"
   - If you add a Microsoft Azure OpenAI Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azureopenai.msgnode and an attribute applicationConnectorType="azureopenai"
   - If you add a Microsoft Azure Service Bus Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_azureservicebus.msgnode and an attribute applicationConnectorType="azureservicebus"
   - If you add a Microsoft Azure Service Bus Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azureservicebus.msgnode and an attribute applicationConnectorType="azureservicebus"
   - If you add a Microsoft Dynamics 365 for Finance and Operations Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msdynamicsfando.msgnode and an attribute applicationConnectorType="msdynamicsfando"
   - If you add a Microsoft Dynamics 365 for Sales Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msdynamicscrmrest.msgnode and an attribute applicationConnectorType="msdynamicscrmrest"
   - If you add a Microsoft Entra ID Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_azuread.msgnode and an attribute applicationConnectorType="azuread"
   - If you add a Microsoft Entra ID Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_azuread.msgnode and an attribute applicationConnectorType="azuread"
   - If you add a Microsoft Excel Online Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msexcel.msgnode and an attribute applicationConnectorType="msexcel"
   - If you add a Microsoft Excel Online Request node to a message flow you **MUST** read the skill guidance in MicrosoftExcelOnline.md to help determine the node properties	 
   - If you add a Microsoft Excel Online Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_msexcel.msgnode and an attribute applicationConnectorType="msexcel"
   - If you add a Microsoft Excel Online Input node to a message flow you **MUST** read the skill guidance in MicrosoftExcelOnline.md to help determine the node properties
   - If you add a Microsoft Exchange Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_msexchange.msgnode and an attribute applicationConnectorType="msexchange"
   - If you add a Microsoft Exchange Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msexchange.msgnode and an attribute applicationConnectorType="msexchange"
   - If you add a Microsoft OneDrive for Business Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msonedrive.msgnode and an attribute applicationConnectorType="msonedrive"
   - If you add a Microsoft OneNote Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_msonenote.msgnode and an attribute applicationConnectorType="msonenote"
   - If you add a Microsoft Power BI Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_mspowerbi.msgnode and an attribute applicationConnectorType="mspowerbi"
   - If you add a Microsoft SharePoint Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_mssharepoint.msgnode and an attribute applicationConnectorType="mssharepoint"
   - If you add a Microsoft SharePoint Request node to a message flow you **MUST** read the skill guidance in MicrosoftSharePoint.md to help determine the node properties	 
   - If you add a Microsoft SharePoint Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_mssharepoint.msgnode and an attribute applicationConnectorType="mssharepoint"
   - If you add a Microsoft SharePoint Input node to a message flow you **MUST** read the skill guidance in MicrosoftSharePoint.md to help determine the node properties
   - If you add a Microsoft Teams Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_msteams.msgnode and an attribute applicationConnectorType="msteams"
   - If you add a Microsoft Teams Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefixf ComIbmApplicationConnectorRequest_msteams.msgnode and an attribute applicationConnectorType="msteams"
   - If you add a Microsoft To Do Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_mstodo.msgnode and an attribute applicationConnectorType="mstodo"
   - If you add a Microsoft Viva Engage Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_yammer.msgnode and an attribute applicationConnectorType="yammer"
   - If you add a Microsoft Viva Engage Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_yammer.msgnode and an attribute applicationConnectorType="yammer"
   - If you add a Milvus Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_milvus.msgnode and an attribute applicationConnectorType="milvus"
   - If you add a monday.com Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_mondaydotcom.msgnode and an attribute applicationConnectorType="mondaydotcom"
   - If you add a monday.com Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_mondaydotcom.msgnode and an attribute applicationConnectorType="mondaydotcom"
   - If you add a MQTTSubscribe node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of com_ibm_connector_mqtt_ComIbmEventInput.msgnode and an attribute connectorName="MQTT"
   - If you add a MQTTPublish node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of com_ibm_connector_mqtt_ComIbmOutput.msgnode and an attribute connectorName="MQTT"
   - If you add a .NETInput node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmDotNetInput.msgnode
   - If you add a Oracle E-Business Suite Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_oracleebs.msgnode and an attribute applicationConnectorType="oracleebs"
   - If you add a Oracle Human Capital Management Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_oraclehcm.msgnode and an attribute applicationConnectorType="oraclehcm"
   - If you add a Oracle Human Capital Management Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_oraclehcm.msgnode and an attribute applicationConnectorType="oraclehcm"
   - If you add a JDEdwards Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJDEdwardsInput.msgnode
   - If you add a JDEdwards Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmJDEdwardsRequest.msgnode
   - If you add a PeopleSoft Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmPeopleSoftInput.msgnode
   - If you add a PeopleSoft Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmPeopleSoftRequest.msgnode
   - If you add a Siebel Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSiebelInput.msgnode
   - If you add a Siebel Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSiebelRequest.msgnode
   - If you add a Pinecone Vector Database Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_pineconedb.msgnode and an attribute applicationConnectorType="pineconedb"  
   - If you add a Redis Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_rediscache.msgnode and an attribute applicationConnectorType="rediscache"
   - If you add a Redis Request node to a message flow you **MUST** read the skill guidance in Redis.md to help determine the node properties   
   - If you add a REST Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmRESTRequest.msgnode
   - If you add a REST Async Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmRESTAsyncRequest.msgnode
   - If you add a REST Async Response node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmRESTAsyncResponse.msgnode
   - If you add a App Connect REST Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmAppConnectRESTRequest.msgnode 
   - If you add a Salesforce Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_salesforce.msgnode and an attribute applicationConnectorType="salesforce"   
   - If you add a Salesforce Request node to a message flow you **MUST** read the skill guidance in Salesforce.md to help determine the node properties	 
   - If you add a Salesforce Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_salesforce.msgnode and an attribute applicationConnectorType="salesforce"
   - If you add a Salesforce Input node to a message flow you **MUST** read the skill guidance in Salesforce.md to help determine the node properties   
   - If you add a Salesforce Request (no discovery) node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of com_ibm_connector_salesforce_ComIbmRequest.msgnode and an attribute connectorName="iib-salesforce-connector"
   - If you add a Salesforce Account Engagement Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_salesforceae.msgnode and an attribute applicationConnectorType="salesforceae"
   - If you add a Salesforce Commerce Cloud Digital Data Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_sfcommerceclouddata.msgnode and an attribute applicationConnectorType="sfcommerceclouddata"
   - If you add a Salesforce Commerce Cloud Digital Data Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_sfcommerceclouddata.msgnode and an attribute applicationConnectorType="sfcommerceclouddata"
   - If you add a Salesforce Marketing Cloud Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_salesforcemc.msgnode and an attribute applicationConnectorType="salesforcemc"
   - If you add a SAP Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSAPInput.msgnode
   - If you add a SAP Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSAPRequest.msgnode
   - If you add a SAP Reply node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSAPReply.msgnode
   - If you add a SAP OData Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_sapodata.msgnode and an attribute applicationConnectorType="sapodata"
   - If you add a SAP Ariba Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_sapariba.msgnode and an attribute applicationConnectorType="sapariba"
   - If you add a SAP S4 HANA Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_saps4hana.msgnode and an attribute applicationConnectorType="saps4hana"
   - If you add a SAP S4 HANA Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_saps4hana.msgnode and an attribute applicationConnectorType="saps4hana"
   - If you add a SAP SuccessFactors Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_sapsuccessfactors.msgnode and an attribute applicationConnectorType="sapsuccessfactors"
   - If you add a SAP SuccessFactors Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_sapsuccessfactors.msgnode and an attribute applicationConnectorType="sapsuccessfactors"
   - If you add a ServiceNow Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_servicenow.msgnode and an attribute applicationConnectorType="servicenow"
   - If you add a ServiceNow Request node to a message flow you **MUST** read the skill guidance in ServiceNow.md to help determine the node properties	 
   - If you add a ServiceNow Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_servicenow.msgnode and an attribute applicationConnectorType="servicenow"
   - If you add a ServiceNow Input node to a message flow you **MUST** read the skill guidance in ServiceNow.md to help determine the node properties
   - If you add a Shopify Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_shopify.msgnode and an attribute applicationConnectorType="shopify"
   - If you add a Shopify Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_shopify.msgnode and an attribute  applicationConnectorType="shopify"
   - If you add a Slack Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_slack.msgnode and an attribute applicationConnectorType="slack"
   - If you add a Slack Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_slack.msgnode and an attribute applicationConnectorType="slack"
   - If you add a Snowflake Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_snowflake.msgnode and an attribute applicationConnectorType="snowflake"
   - If you add a SOAP Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSOAPInput.msgnode
   - If you add a SOAP Reply node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSOAPReply.msgnode
   - If you add a SOAP Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSOAPRequest.msgnode
   - If you add a SOAP Async Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSOAPAsyncRequest.msgnode
   - If you add a SOAP Async Response node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSOAPAsyncResponse.msgnode
   - If you add a SOAP Envelope node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSOAPEnvelope.msgnode
   - If you add a SOAP Extract node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmSOAPExtract.msgnode
   - If you add a Registry Lookup node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of SRRetrieveEntity.msgnode
   - If you add a Endpoint Lookup node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of SRRetrieveITService.msgnode
   - If you add a Splunk Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_splunk.msgnode and an attribute applicationConnectorType="splunk"
   - If you add a Square Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_square.msgnode and an attribute  applicationConnectorType="square"
   - If you add a SurveyMonkey Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_surveymonkey.msgnode and an attribute applicationConnectorType="surveymonkey"
   - If you add a SurveyMonkey Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_surveymonkey.msgnode and an attribute applicationConnectorType="surveymonkey"
   - If you add a TCPIP Client Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTCPIPClientInput.msgnode
   - If you add a TCPIP Client Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTCPIPClientOutput.msgnode
   - If you add a TCPIP Client Receive node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTCPIPClientReceive.msgnode
   - If you add a TCPIP Server Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTCPIPServerInput.msgnode
   - If you add a TCPIP Server Output node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTCPIPServerOutput.msgnode
   - If you add a TCPIP Server Receive node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmTCPIPServerReceive.msgnode
   - If you add a The Weather Company Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_ibmtwc.msgnode and an attribute applicationConnectorType="ibmtwc"
   - If you add a Toggl Track Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_toggltrack.msgnode and an attribute applicationConnectorType="toggltrack"
   - If you add a Toggl Track Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_toggltrack.msgnode and an attribute applicationConnectorType="toggltrack"
   - If you add a Trello Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_trello.msgnode and an attribute applicationConnectorType="trello"
   - If you add a Twilio Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_twilio.msgnode and an attribute applicationConnectorType="twilio"
   - If you add a UKG Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_kronos.msgnode and an attribute applicationConnectorType="kronos"
   - If you add a Vespa Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_vespa.msgnode and an attribute applicationConnectorType="vespa"
   - If you add a WordPress Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_wordpress.msgnode and an attribute applicationConnectorType="wordpress"
   - If you add a Workday Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_workday.msgnode and an attribute applicationConnectorType="workday"
   - If you add a Wrike Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_wrike.msgnode and an attribute applicationConnectorType="wrike"
   - If you add a Wrike Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_wrike.msgnode and an attribute applicationConnectorType="wrike"
   - If you add a Wufoo Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_wufoo.msgnode and an attribute applicationConnectorType="wufoo"
   - If you add a Wufoo Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_wufoo.msgnode and an attribute applicationConnectorType="wufoo"
   - If you add a Yapily Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_yapily.msgnode and an attribute applicationConnectorType="yapily"
   - If you add a Zendesk Service Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_zendeskservice.msgnode and an attribute applicationConnectorType="zendeskservice"
   - If you add a Zendesk Service Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_zendeskservice.msgnode and an attribute applicationConnectorType="zendeskservice"
   - If you add a Zoho Books Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_zohobooks.msgnode and an attribute applicationConnectorType="zohobooks"
   - If you add a Zoho Books Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_zohobooks.msgnode and an attribute applicationConnectorType="zohobooks"
   - If you add a Zoho CRM Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_zohocrm.msgnode and an attribute applicationConnectorType="zohocrm"
   - If you add a Zoho CRM Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_zohocrm.msgnode and an attribute applicationConnectorType="zohocrm"
   - If you add a Zoho Inventory Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_zohoinventory.msgnode and an attribute applicationConnectorType="zohoinventory"
   - If you add a Zoho Recruit Input node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorInput_zohorecruit.msgnode and an attribute applicationConnectorType="zohorecruit"
   - If you add a Zoho Recruit Request node to a message flow, it **MUST** have an xmi:type attribute using the namespace prefix of ComIbmApplicationConnectorRequest_zohorecruit.msgnode and an attribute applicationConnectorType="zohorecruit"
   - If you add a message flow node to a message flow which has an xmi:type attribute with a namespace prefix that starts with ComIbmApplicationConnector 
   - When generating or reviewing ACE artifacts, ensure they follow IBM best practices, are well-documented, handle errors gracefully, and are optimized for performance and maintainability.",

6. **Create an ESQL file**
   - If the message flow contains a Compute node then create an associated ESQL file in the Application project
   - Use efficient ESQL coding techniques
   - Ensure the proper use of REFERENCE vs VALUE
   - Be aware of memory management and performance optimization

# Task Completion Checklist

Before using attempt_completion, verify:
- [ ] All requested artifacts created
- [ ] Import instructions message included (if any new ACE Toolkit project has been created)

