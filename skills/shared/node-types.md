# ACE Node Type Reference

## Purpose
This document contains the canonical mapping from ACE node names to the `xmi:type` values that must be used in `.msgflow` files.

## How to use this document
- Treat this file as the canonical node type reference for this repository.
- Some entries provide the complete `xmi:type` value directly.
- Other entries require the namespace prefix of a specific `.msgnode` definition. For those entries, validate the exact namespace prefix against the ACE Message Flow schema for the user's version.
- For connector nodes, also read the relevant connector guidance file.

## Rules
- Use the exact validated `xmi:type` values.
- Do not invent namespace prefixes.
- Do not rely on old example `.msgflow` files as the source of truth.

### Finding Unknown Property Names
When you encounter a message flow node property name that you don't recognize:

1. **Search MessageFlowUI.xsd first**: Look for the user's property description (e.g., "Generate default HTTP headers from input")
2. **Extract the property ID**: Find the attribute ID (e.g., `id="Property.generateDefaultHttpHeaders"`)
3. **Cross-reference MessageFlow.xsd**: Search for the property ID to find the actual XML attribute name (e.g., `name="generateDefaultHttpHeaders"`)
4. **Check the data type and default**: Note the type (boolean, string, etc.) and default value if specified

**Example workflow:**
- User asks: "Set 'Generate default HTTP headers from input' to false"
- Search MessageFlowUI.xsd for: "Generate default HTTP headers from input"
- Find: `<xsd:attribute id="Property.generateDefaultHttpHeaders" name="Property.generateDefaultHttpHeaders">`
- Search MessageFlow.xsd for: "generateDefaultHttpHeaders"
- Find: `<xsd:attribute id="Property.generateDefaultHttpHeaders" name="generateDefaultHttpHeaders" type="xsd:boolean" default="true"/>`
- Result: Add attribute `generateDefaultHttpHeaders="false"` to the node

**XSD File Locations:**
- The XSD files can be found in the ACE installation for example on Windows at `C:\Program Files\IBM\ACE\13.0.n.0\common\schemas\MessageFlow`
- If you do not have access to the XSD files you should ask the user to provide them from the above location.

---

## Subflow nodes
- Subflow nodes are references to content defined in .subflow files
- When an ACE Toolkit `.msgflow` file contains a subflow node, then the xmi:type of the subflow node is a reference to the actual .subflow such as `ExampleSubflow.subflow:FCMComposite_1`
- If the subflow is located in a broker schema (subdirectory of its project) then this should also be included in the xmi:type such as `ExampleBrokerSchema_ExampleSubflow.subflow:FCMComposite_1` where ExampleBrokerSchema is the name of the broker schema
- There should then be an xmlns prefix declaration such as `xmlns:ExampleBrokerSchema_ExampleSubflow.subflow="ExampleBrokerSchema/ExampleSubflow.subflow"`
- Subflow Input node → `xmi:type="eflow:FCMSource"`
- Subflow Output node → `xmi:type="eflow:FCMSink"`

## Callable flow nodes
- Callable Input node → namespace prefix of `ComIbmCallableFlowInput.msgnode`
- Callable Reply node → namespace prefix of `ComIbmCallableFlowReply.msgnode`
- Callable Flow Invoke node → namespace prefix of `ComIbmCallableFlowInvoke.msgnode`
- Callable Flow Async Invoke node → namespace prefix of `ComIbmCallableFlowAsyncInvoke.msgnode`
- Callable Flow Async Response node → namespace prefix of `ComIbmCallableFlowAsyncResponse.msgnode`

## Error handling and tracing nodes
- Throw node → namespace prefix of `ComIbmThrow.msgnode`
- Try Catch node → namespace prefix of `ComIbmTryCatch.msgnode`
  - **Note:** Try Catch nodes have one input terminal named `InTerminal.in` and two output terminals named `OutTerminal.try` and `OutTerminal.catch`
- Trace node → namespace prefix of `ComIbmTrace.msgnode`
- Validate node → namespace prefix of `ComIbmValidate.msgnode`
- Log node → namespace prefix of `ComIbmLog.msgnode`

## Aggregation nodes
- Aggregate Control node → namespace prefix of `ComIbmAggregateControl.msgnode`
- Aggregate Reply node → namespace prefix of `ComIbmAggregateReply.msgnode`
- Aggregate Request node → namespace prefix of `ComIbmAggregateRequest.msgnode`
- Collector node → namespace prefix of `ComIbmCollector.msgnode`
- Group Scatter node → namespace prefix of `ComIbmGroupScatter.msgnode`
- Group Gather node → namespace prefix of `ComIbmGroupGather.msgnode`
- Group Complete node → namespace prefix of `ComIbmGroupComplete.msgnode`
- Resequence node → namespace prefix of `ComIbmReSequence.msgnode`
- Sequence node → namespace prefix of `ComIbmSequence.msgnode`

## Routing and control nodes
- Filter node → namespace prefix of `ComIbmFilter.msgnode`
- Label node → namespace prefix of `ComIbmLabel.msgnode`
- Route To Label node → namespace prefix of `ComIbmRouteToLabel.msgnode`
- Route node → namespace prefix of `ComIbmRoute.msgnode`
- Flow Order node → namespace prefix of `ComIbmFlowOrder.msgnode`
- Pass Through node → namespace prefix of `ComIbmPassthru.msgnode`
- Security PEP node → namespace prefix of `ComIbmSecurityPEP.msgnode`

## Scheduling and timeout nodes
- Timeout Control node → namespace prefix of `ComIbmTimeoutControl.msgnode`
- Timeout Notification node → namespace prefix of `ComIbmTimeoutNotification.msgnode`
- Scheduler node → namespace prefix of `ComIbmScheduler.msgnode`

## Compute and transformation nodes
- Compute node → namespace prefix of `ComIbmCompute.msgnode`
- Java Compute node → namespace prefix of `ComIbmJavaCompute.msgnode`
- .NET Compute node → namespace prefix of `ComIbmDotNetCompute.msgnode`
- JSONata Mapping node → namespace prefix of `ComIbmJSONataMapping.msgnode`
- Mapping node → namespace prefix of `ComIbmMSLMapping.msgnode`
- XSL Transform node → namespace prefix of `ComIbmXslMqsi.msgnode`
- Reset Content Descriptor node → namespace prefix of `ComIbmResetContentDescriptor.msgnode`

## HTTP nodes
> **⚠ Naming trap:** The ACE Toolkit UI labels these nodes "HTTP Input", "HTTP Reply", and "HTTP Request", but the underlying `.msgnode` filenames use the `ComIbmWS*` prefix — **not** `ComIbmHTTP*`. Always use the `ComIbmWS*` variants listed here. Using `ComIbmHTTPInput` or `ComIbmHTTPReply` will cause "Message node cannot be located" errors and incorrect icons at runtime.

- HTTP Input node → namespace prefix of `ComIbmWSInput.msgnode`
- HTTP Reply node → namespace prefix of `ComIbmWSReply.msgnode`
- HTTP Request node → namespace prefix of `ComIbmWSRequest.msgnode`
  - **Note:** HTTP Request nodes require a `URLSpecifier` attribute that defines the Web Service URL that should be invoked. If not provided, ask the user for their preference.
- HTTP Header node → namespace prefix of `ComIbmHTTPHeader.msgnode`
- HTTP Async Request node → namespace prefix of `ComIbmHTTPAsyncRequest.msgnode`
- HTTP Async Response node → namespace prefix of `ComIbmHTTPAsyncResponse.msgnode`

## MQ nodes
- MQ Input node → namespace prefix of `ComIbmMQInput.msgnode`
  - **Note:** MQ Input nodes require a `queueName` attribute. If not provided, ask the user for their preference.
- MQ Output node → namespace prefix of `ComIbmMQOutput.msgnode`
- MQ Reply node → namespace prefix of `ComIbmMQReply.msgnode`
- MQ Get node → namespace prefix of `ComIbmMQGet.msgnode`
- MQ Header node → namespace prefix of `ComIbmMQHeader.msgnode`
- Publication node → namespace prefix of `ComIbmPublication.msgnode`

## File nodes
- File Input node → namespace prefix of `ComIbmFileInput.msgnode`
- File Output node → namespace prefix of `ComIbmFileOutput.msgnode`
- File Read node → namespace prefix of `ComIbmFileRead.msgnode`
- File Exists node → namespace prefix of `ComIbmFileExists.msgnode`
- File Iterator node → namespace prefix of `ComIbmFileIterator.msgnode`

## Email nodes
- Email Input node → namespace prefix of `ComIbmEmailInput.msgnode`
- Email Output node → namespace prefix of `ComIbmEmailOutput.msgnode`

## JMS nodes
- JMS Input node → namespace prefix of `ComIbmJMSClientInput.msgnode`
- JMS Output node → namespace prefix of `ComIbmJMSClientOutput.msgnode`
- JMS Reply node → namespace prefix of `ComIbmJMSClientReply.msgnode`
- JMS Receive node → namespace prefix of `ComIbmJMSClientReceive.msgnode`
- JMS Header node → namespace prefix of `ComIbmJMSHeader.msgnode`

## Kafka nodes
- Kafka Consumer node → namespace prefix of `ComIbmKafkaMsgConsumer.msgnode`
- Kafka Producer node → namespace prefix of `ComIbmKafkaMsgProducer.msgnode`
- Kafka Read node → namespace prefix of `ComIbmKafkaMsgRead.msgnode`

## Database nodes
- Database Input node → namespace prefix of `ComIbmDatabaseInput.msgnode`
- Database node → namespace prefix of `ComIbmDatabase.msgnode`
- Database Retrieve node → namespace prefix of `ComIbmDatabaseRetrieve.msgnode`
- Database Route node → namespace prefix of `ComIbmDatabaseRoute.msgnode`
- Change Data Capture node → namespace prefix of `ComIbmChangeDataCapture.msgnode`

## IBM enterprise middleware nodes
- CICS Request node → namespace prefix of `ComIbmCICSIPICRequest.msgnode`
- IMS Request node → namespace prefix of `ComIbmIMSRequest.msgnode`
- CORBA Request node → namespace prefix of `ComIbmCORBARequest.msgnode`
- ODM Rules node → namespace prefix of `ComIbmODMRules.msgnode`
- CD Input node → namespace prefix of `ComIbmCDInput.msgnode`
- CD Output node → namespace prefix of `ComIbmCDOutput.msgnode`
- FTE Input node → namespace prefix of `ComIbmFTEInput.msgnode`
- FTE Output node → namespace prefix of `ComIbmFTEOutput.msgnode`

---

## Connector nodes
Connector nodes usually use the `applicationConnectorType` attribute in addition to their `xmi:type`.
For connector-specific required attributes, allowed operations, and policies, read the relevant connector guidance file listed in the Connector references section below.
Some older connector styles use `connectorName` instead of `applicationConnectorType`; preserve those values exactly where documented below.

### Amazon AWS Connectors
- Amazon CloudWatch Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazoncloudwatch.msgnode` + `applicationConnectorType="amazoncloudwatch"`
- Amazon DynamoDB Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazondynamodb.msgnode` + `applicationConnectorType="amazondynamodb"`
- Amazon EC2 Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazonec2.msgnode` + `applicationConnectorType="amazonec2"`
- Amazon EventBridge Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazoneventbridge.msgnode` + `applicationConnectorType="amazoneventbridge"`
- Amazon EventBridge Input node → namespace prefix of `ComIbmApplicationConnectorInput_amazoneventbridge.msgnode` + `applicationConnectorType="amazoneventbridge"`
- Amazon Kinesis Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazonkinesis.msgnode` + `applicationConnectorType="amazonkinesis"`
- Amazon RDS Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazonrds.msgnode` + `applicationConnectorType="amazonrds"`
- Amazon S3 Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazons3.msgnode` + `applicationConnectorType="amazons3"` → see `skills/shared/connectors/amazon-s3.md`
- Amazon SES Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazonses.msgnode` + `applicationConnectorType="amazonses"`
- Amazon SNS Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazonsns.msgnode` + `applicationConnectorType="amazonsns"`
- Amazon SQS Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazonsqs.msgnode` + `applicationConnectorType="amazonsqs"`
- Amazon SQS Input node → namespace prefix of `ComIbmApplicationConnectorInput_amazonsqs.msgnode` + `applicationConnectorType="amazonsqs"`
- AWS Lambda Request node → namespace prefix of `ComIbmApplicationConnectorRequest_amazonlambda.msgnode` + `applicationConnectorType="amazonlambda"`

### Box
- Box Request node → namespace prefix of `ComIbmApplicationConnectorRequest_box.msgnode` + `applicationConnectorType="box"` → see `skills/shared/connectors/box.md`

### Dropbox
- Dropbox Request node → namespace prefix of `ComIbmApplicationConnectorRequest_dropbox.msgnode` + `applicationConnectorType="dropbox"` → see `skills/shared/connectors/dropbox.md`

### GitHub
- GitHub Request node → namespace prefix of `ComIbmApplicationConnectorRequest_github.msgnode` + `applicationConnectorType="github"` → see `skills/shared/connectors/github.md`
- GitHub Input node → namespace prefix of `ComIbmApplicationConnectorInput_github.msgnode` + `applicationConnectorType="github"` → see `skills/shared/connectors/github.md`

### GitLab
- GitLab Request node → namespace prefix of `ComIbmApplicationConnectorRequest_gitlab.msgnode` + `applicationConnectorType="gitlab"` → see `skills/shared/connectors/gitlab.md`
- GitLab Input node → namespace prefix of `ComIbmApplicationConnectorInput_gitlab.msgnode` + `applicationConnectorType="gitlab"` → see `skills/shared/connectors/gitlab.md`

### Google
- Google Analytics Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googleanalytics4.msgnode` + `applicationConnectorType="googleanalytics4"`
- Google Calendar Input node → namespace prefix of `ComIbmApplicationConnectorInput_googlecalendar.msgnode` + `applicationConnectorType="googlecalendar"`
- Google Calendar Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlecalendar.msgnode` + `applicationConnectorType="googlecalendar"`
- Google Chat Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlechat.msgnode` + `applicationConnectorType="googlechat"`
- Google Cloud BigQuery Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlebigquery.msgnode` + `applicationConnectorType="googlebigquery"`
- Google Cloud PubSub Input node → namespace prefix of `ComIbmApplicationConnectorInput_googlepubsub.msgnode` + `applicationConnectorType="googlepubsub"`
- Google Cloud PubSub Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlepubsub.msgnode` + `applicationConnectorType="googlepubsub"`
- Google Cloud Storage Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlecloudstorage.msgnode` + `applicationConnectorType="googlecloudstorage"` → see `skills/shared/connectors/google-cloud-storage.md`
- Google Contacts Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlecontacts.msgnode` + `applicationConnectorType="googlecontacts"`
- Google Drive Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googledrive.msgnode` + `applicationConnectorType="googledrive"`
- Google Gemini Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlegemini.msgnode` + `applicationConnectorType="googlegemini"`
- Google Groups Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlegroups.msgnode` + `applicationConnectorType="googlegroups"`
- Google Sheets Input node → namespace prefix of `ComIbmApplicationConnectorInput_googlesheet.msgnode` + `applicationConnectorType="googlesheet"`
- Google Sheets Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googlesheet.msgnode` + `applicationConnectorType="googlesheet"`
- Google Tasks Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googletasks.msgnode` + `applicationConnectorType="googletasks"`
- Google Translate Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googletranslate.msgnode` + `applicationConnectorType="googletranslate"`
- Google Universal Analytics Request node → namespace prefix of `ComIbmApplicationConnectorRequest_googleanalytics.msgnode` + `applicationConnectorType="googleanalytics"`

### HubSpot
- HubSpot CRM Request node → namespace prefix of `ComIbmApplicationConnectorRequest_hubspotcrm.msgnode` + `applicationConnectorType="hubspotcrm"`
- HubSpot Marketing Input node → namespace prefix of `ComIbmApplicationConnectorInput_hubspotmarketing.msgnode` + `applicationConnectorType="hubspotmarketing"`
- HubSpot Marketing Request node → namespace prefix of `ComIbmApplicationConnectorRequest_hubspotmarketing.msgnode` + `applicationConnectorType="hubspotmarketing"`

### IBM
- IBM Aspera Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ibmaspera.msgnode` + `applicationConnectorType="ibmaspera"`
- IBM Cloud Object Storage S3 Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ibmcoss3.msgnode` + `applicationConnectorType="ibmcoss3"`
- IBM Cloudant Request node → namespace prefix of `ComIbmApplicationConnectorRequest_cloudantdb.msgnode` + `applicationConnectorType="cloudantdb"` → see `skills/shared/connectors/ibm-cloudant.md`
- IBM Engineering Workflow Management Input node → namespace prefix of `ComIbmApplicationConnectorInput_ibmewm.msgnode` + `applicationConnectorType="ibmewm"`
- IBM Engineering Workflow Management Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ibmewm.msgnode` + `applicationConnectorType="ibmewm"`
- IBM FileNet Content Manager Request node → namespace prefix of `ComIbmApplicationConnectorRequest_filenet.msgnode` + `applicationConnectorType="filenet"`
- IBM Food Trust Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ift.msgnode` + `applicationConnectorType="ift"`
- IBM Maximo Input node → namespace prefix of `ComIbmApplicationConnectorInput_maximo.msgnode` + `applicationConnectorType="maximo"`
- IBM Maximo Request node → namespace prefix of `ComIbmApplicationConnectorRequest_maximo.msgnode` + `applicationConnectorType="maximo"`
- IBM OpenPages with Watson Input node → namespace prefix of `ComIbmApplicationConnectorInput_ibmopenpages.msgnode` + `applicationConnectorType="ibmopenpages"`
- IBM OpenPages with Watson Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ibmopenpages.msgnode` + `applicationConnectorType="ibmopenpages"`
- IBM Planning Analytics Request node → namespace prefix of `ComIbmApplicationConnectorRequest_planninganalytics.msgnode` + `applicationConnectorType="planninganalytics"`
- IBM Sterling Intelligent Promising Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ibmsterlingiv.msgnode` + `applicationConnectorType="ibmsterlingiv"`
- IBM Targetprocess Input node → namespace prefix of `ComIbmApplicationConnectorInput_apptiotargetprocess.msgnode` + `applicationConnectorType="apptiotargetprocess"`
- IBM Targetprocess Request node → namespace prefix of `ComIbmApplicationConnectorRequest_apptiotargetprocess.msgnode` + `applicationConnectorType="apptiotargetprocess"`
- IBM Watson Discovery Request node → namespace prefix of `ComIbmApplicationConnectorRequest_watsondiscovery.msgnode` + `applicationConnectorType="watsondiscovery"`
- IBM watsonx.ai Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ibmwatsonxai.msgnode` + `applicationConnectorType="ibmwatsonxai"`
- IBM zOS Connect Request node → namespace prefix of `ComIbmApplicationConnectorRequest_zosconnect.msgnode` + `applicationConnectorType="zosconnect"`

### Jira
- Jira Request node → namespace prefix of `ComIbmApplicationConnectorRequest_jira.msgnode` + `applicationConnectorType="jira"` → see `skills/shared/connectors/jira.md`
- Jira Input node → namespace prefix of `ComIbmApplicationConnectorInput_jira.msgnode` + `applicationConnectorType="jira"` → see `skills/shared/connectors/jira.md`

### Jenkins
- Jenkins Request node → namespace prefix of `ComIbmApplicationConnectorRequest_jenkins.msgnode` + `applicationConnectorType="jenkins"` → see `skills/shared/connectors/jenkins.md`

### Microsoft
- Microsoft Active Directory Input node → namespace prefix of `ComIbmApplicationConnectorInput_msad.msgnode` + `applicationConnectorType="msad"`
- Microsoft Active Directory Request node → namespace prefix of `ComIbmApplicationConnectorRequest_msad.msgnode` + `applicationConnectorType="msad"`
- Microsoft Azure Blob Storage Request node → namespace prefix of `ComIbmApplicationConnectorRequest_azureblobstorage.msgnode` + `applicationConnectorType="azureblobstorage"` → see `skills/shared/connectors/microsoft-azure-blob-storage.md`
- Microsoft Azure Cosmos DB Request node → namespace prefix of `ComIbmApplicationConnectorRequest_azurecosmosdb.msgnode` + `applicationConnectorType="azurecosmosdb"`
- Microsoft Azure DevOps Input node → namespace prefix of `ComIbmApplicationConnectorInput_azuredevops.msgnode` + `applicationConnectorType="azuredevops"`
- Microsoft Azure DevOps Request node → namespace prefix of `ComIbmApplicationConnectorRequest_azuredevops.msgnode` + `applicationConnectorType="azuredevops"`
- Microsoft Azure Event Hubs Input node → namespace prefix of `ComIbmApplicationConnectorInput_azureeventhub.msgnode` + `applicationConnectorType="azureeventhub"`
- Microsoft Azure Event Hubs Request node → namespace prefix of `ComIbmApplicationConnectorRequest_azureeventhub.msgnode` + `applicationConnectorType="azureeventhub"`
- Microsoft Azure OpenAI Request node → namespace prefix of `ComIbmApplicationConnectorRequest_azureopenai.msgnode` + `applicationConnectorType="azureopenai"`
- Microsoft Azure Service Bus Input node → namespace prefix of `ComIbmApplicationConnectorInput_azureservicebus.msgnode` + `applicationConnectorType="azureservicebus"`
- Microsoft Azure Service Bus Request node → namespace prefix of `ComIbmApplicationConnectorRequest_azureservicebus.msgnode` + `applicationConnectorType="azureservicebus"`
- Microsoft Excel Online Request node → namespace prefix of `ComIbmApplicationConnectorRequest_msexcel.msgnode` + `applicationConnectorType="msexcel"` → see `skills/shared/connectors/microsoft-excel-online.md`
- Microsoft Excel Online Input node → namespace prefix of `ComIbmApplicationConnectorInput_msexcel.msgnode` + `applicationConnectorType="msexcel"` → see `skills/shared/connectors/microsoft-excel-online.md`
- Microsoft SharePoint Request node → namespace prefix of `ComIbmApplicationConnectorRequest_mssharepoint.msgnode` + `applicationConnectorType="mssharepoint"` → see `skills/shared/connectors/microsoft-sharepoint.md`
- Microsoft SharePoint Input node → namespace prefix of `ComIbmApplicationConnectorInput_mssharepoint.msgnode` + `applicationConnectorType="mssharepoint"` → see `skills/shared/connectors/microsoft-sharepoint.md`

### Redis
- Redis Request node → namespace prefix of `ComIbmApplicationConnectorRequest_rediscache.msgnode` + `applicationConnectorType="rediscache"` → see `skills/shared/connectors/redis.md`

### Salesforce
- Salesforce Request node → namespace prefix of `ComIbmApplicationConnectorRequest_salesforce.msgnode` + `applicationConnectorType="salesforce"` → see `skills/shared/connectors/salesforce.md`
- Salesforce Input node → namespace prefix of `ComIbmApplicationConnectorInput_salesforce.msgnode` + `applicationConnectorType="salesforce"` → see `skills/shared/connectors/salesforce.md`

### ServiceNow
- ServiceNow Request node → namespace prefix of `ComIbmApplicationConnectorRequest_servicenow.msgnode` + `applicationConnectorType="servicenow"` → see `skills/shared/connectors/service-now.md`
- ServiceNow Input node → namespace prefix of `ComIbmApplicationConnectorInput_servicenow.msgnode` + `applicationConnectorType="servicenow"` → see `skills/shared/connectors/service-now.md`

### Other Connectors
- Anaplan Request node → namespace prefix of `ComIbmApplicationConnectorRequest_anaplan.msgnode` + `applicationConnectorType="anaplan"`
- Apache Pulsar Request node → namespace prefix of `ComIbmApplicationConnectorRequest_apachepulsar.msgnode` + `applicationConnectorType="apachepulsar"`
- Apache Pulsar Input node → namespace prefix of `ComIbmApplicationConnectorInput_apachepulsar.msgnode` + `applicationConnectorType="apachepulsar"`
- Asana Input node → namespace prefix of `ComIbmApplicationConnectorInput_asana.msgnode` + `applicationConnectorType="asana"`
- Asana Request node → namespace prefix of `ComIbmApplicationConnectorRequest_asana.msgnode` + `applicationConnectorType="asana"`
- Astra DB Input node → namespace prefix of `ComIbmApplicationConnectorInput_astradb.msgnode` + `applicationConnectorType="astradb"`
- Astra DB Request node → namespace prefix of `ComIbmApplicationConnectorRequest_astradb.msgnode` + `applicationConnectorType="astradb"`
- BambooHR Request node → namespace prefix of `ComIbmApplicationConnectorRequest_bamboohr.msgnode` + `applicationConnectorType="bamboohr"`
- Businessmap Request node → namespace prefix of `ComIbmApplicationConnectorRequest_businessmap.msgnode` + `applicationConnectorType="businessmap"`
- Businessmap Input node → namespace prefix of `ComIbmApplicationConnectorInput_businessmap.msgnode` + `applicationConnectorType="businessmap"`
- Calendly Request node → namespace prefix of `ComIbmApplicationConnectorRequest_calendly.msgnode` + `applicationConnectorType="calendly"`
- ClickSend Input node → namespace prefix of `ComIbmApplicationConnectorInput_clicksend.msgnode` + `applicationConnectorType="clicksend"`
- ClickSend Request node → namespace prefix of `ComIbmApplicationConnectorRequest_clicksend.msgnode` + `applicationConnectorType="clicksend"`
- CMIS Input node → namespace prefix of `ComIbmApplicationConnectorInput_cmis.msgnode` + `applicationConnectorType="cmis"`
- CMIS Request node → namespace prefix of `ComIbmApplicationConnectorRequest_cmis.msgnode` + `applicationConnectorType="cmis"`
- Confluence Request node → namespace prefix of `ComIbmApplicationConnectorRequest_confluence.msgnode` + `applicationConnectorType="confluence"`
- Couchbase Request node → namespace prefix of `ComIbmApplicationConnectorRequest_couchbase.msgnode` + `applicationConnectorType="couchbase"`
- Coupa Request node → namespace prefix of `ComIbmApplicationConnectorRequest_coupa.msgnode` + `applicationConnectorType="coupa"`
- Coupa Input node → namespace prefix of `ComIbmApplicationConnectorInput_coupa.msgnode` + `applicationConnectorType="coupa"`
- Crystal Ball Request node → namespace prefix of `ComIbmApplicationConnectorRequest_crystalball.msgnode` + `applicationConnectorType="crystalball"`
- Databricks Input node → namespace prefix of `ComIbmApplicationConnectorInput_databricks.msgnode` + `applicationConnectorType="databricks"`
- DocuSign Request node → namespace prefix of `ComIbmApplicationConnectorRequest_docusign.msgnode` + `applicationConnectorType="docusign"`
- Eventbrite Input node → namespace prefix of `ComIbmApplicationConnectorInput_eventbrite.msgnode` + `applicationConnectorType="eventbrite"`
- Eventbrite Request node → namespace prefix of `ComIbmApplicationConnectorRequest_eventbrite.msgnode` + `applicationConnectorType="eventbrite"`
- Expensify Request node → namespace prefix of `ComIbmApplicationConnectorRequest_expensify.msgnode` + `applicationConnectorType="expensify"`
- Factorial HR Request node → namespace prefix of `ComIbmApplicationConnectorRequest_factorialhr.msgnode` + `applicationConnectorType="factorialhr"`
- Freshservice Input node → namespace prefix of `ComIbmApplicationConnectorInput_freshservice.msgnode` + `applicationConnectorType="freshservice"`
- Freshservice Request node → namespace prefix of `ComIbmApplicationConnectorRequest_freshservice.msgnode` + `applicationConnectorType="freshservice"`
- Front Input node → namespace prefix of `ComIbmApplicationConnectorInput_front.msgnode` + `applicationConnectorType="front"`
- Front Request node → namespace prefix of `ComIbmApplicationConnectorRequest_front.msgnode` + `applicationConnectorType="front"`
- Gmail Input node → namespace prefix of `ComIbmApplicationConnectorInput_gmail.msgnode` + `applicationConnectorType="gmail"`
- Gmail Request node → namespace prefix of `ComIbmApplicationConnectorRequest_gmail.msgnode` + `applicationConnectorType="gmail"`
- Greenhouse Input node → namespace prefix of `ComIbmApplicationConnectorInput_greenhouse.msgnode` + `applicationConnectorType="greenhouse"`
- Greenhouse Request node → namespace prefix of `ComIbmApplicationConnectorRequest_greenhouse.msgnode` + `applicationConnectorType="greenhouse"`
- Hunter Request node → namespace prefix of `ComIbmApplicationConnectorRequest_hunter.msgnode` + `applicationConnectorType="hunter"`
- Infobip Request node → namespace prefix of `ComIbmApplicationConnectorRequest_infobip.msgnode` + `applicationConnectorType="infobip"`
- Insightly Input node → namespace prefix of `ComIbmApplicationConnectorInput_insightly.msgnode` + `applicationConnectorType="insightly"`
- Insightly Request node → namespace prefix of `ComIbmApplicationConnectorRequest_insightly.msgnode` + `applicationConnectorType="insightly"`
- LDAP Input node → namespace prefix of `ComIbmApplicationConnectorInput_ldap.msgnode` + `applicationConnectorType="ldap"`
- LDAP Request node → namespace prefix of `ComIbmApplicationConnectorRequest_ldap.msgnode` + `applicationConnectorType="ldap"`
- Loop Back Request node → namespace prefix of `com_ibm_connector_loopback_ComIbmRequest.msgnode` + `connectorName="iib-loopback-connector"`
- Magento Input node → namespace prefix of `ComIbmApplicationConnectorInput_magento.msgnode` + `applicationConnectorType="magento"`
- Magento Request node → namespace prefix of `ComIbmApplicationConnectorRequest_magento.msgnode` + `applicationConnectorType="magento"`
- Mailchimp Input node → namespace prefix of `ComIbmApplicationConnectorInput_mailchimp.msgnode` + `applicationConnectorType="mailchimp"`
- Mailchimp Request node → namespace prefix of `ComIbmApplicationConnectorRequest_mailchimp.msgnode` + `applicationConnectorType="mailchimp"`
- Marketo Input node → namespace prefix of `ComIbmApplicationConnectorInput_marketo.msgnode` + `applicationConnectorType="marketo"`
- Marketo Request node → namespace prefix of `ComIbmApplicationConnectorRequest_marketo.msgnode` + `applicationConnectorType="marketo"`

---

## Connector references
- Amazon CloudWatch → [`skills/shared/connectors/amazon-cloudwatch.md`](connectors/amazon-cloudwatch.md)
- Amazon DynamoDB → [`skills/shared/connectors/amazondynamodb.md`](connectors/amazondynamodb.md)
- Amazon EC2 → [`skills/shared/connectors/amazonec2.md`](connectors/amazonec2.md)
- Amazon EventBridge → [`skills/shared/connectors/amazoneventbridge.md`](connectors/amazoneventbridge.md)
- Amazon Kinesis → [`skills/shared/connectors/amazonkinesis.md`](connectors/amazonkinesis.md)
- Amazon Lambda → [`skills/shared/connectors/amazonlambda.md`](connectors/amazonlambda.md)
- Amazon RDS → [`skills/shared/connectors/amazonrds.md`](connectors/amazonrds.md)
- Amazon S3 → [`skills/shared/connectors/amazon-s3.md`](connectors/amazon-s3.md)
- Amazon SES → [`skills/shared/connectors/amazonses.md`](connectors/amazonses.md)
- Amazon SNS → [`skills/shared/connectors/amazonsns.md`](connectors/amazonsns.md)
- Amazon SQS → [`skills/shared/connectors/amazonsqs.md`](connectors/amazonsqs.md)
- Anaplan → [`skills/shared/connectors/anaplan.md`](connectors/anaplan.md)
- Apache Pulsar → [`skills/shared/connectors/apachepulsar.md`](connectors/apachepulsar.md)
- Asana → [`skills/shared/connectors/asana.md`](connectors/asana.md)
- Astra DB → [`skills/shared/connectors/astradb.md`](connectors/astradb.md)
- Azure AD → [`skills/shared/connectors/azuread.md`](connectors/azuread.md)
- Azure Blob Storage → [`skills/shared/connectors/azureblobstorage.md`](connectors/azureblobstorage.md)
- Azure Cosmos DB → [`skills/shared/connectors/azurecosmosdb.md`](connectors/azurecosmosdb.md)
- Azure DevOps → [`skills/shared/connectors/azuredevops.md`](connectors/azuredevops.md)
- Azure Event Hub → [`skills/shared/connectors/azureeventhub.md`](connectors/azureeventhub.md)
- Azure OpenAI → [`skills/shared/connectors/azureopenai.md`](connectors/azureopenai.md)
- Azure Service Bus → [`skills/shared/connectors/azureservicebus.md`](connectors/azureservicebus.md)
- BambooHR → [`skills/shared/connectors/bamboohr.md`](connectors/bamboohr.md)
- Box → [`skills/shared/connectors/box.md`](connectors/box.md)
- Businessmap → [`skills/shared/connectors/businessmap.md`](connectors/businessmap.md)
- Calendly → [`skills/shared/connectors/calendly.md`](connectors/calendly.md)
- ClickSend → [`skills/shared/connectors/clicksend.md`](connectors/clicksend.md)
- Cloudant DB → [`skills/shared/connectors/cloudantdb.md`](connectors/cloudantdb.md)
- CMIS → [`skills/shared/connectors/cmis.md`](connectors/cmis.md)
- Confluence → [`skills/shared/connectors/confluence.md`](connectors/confluence.md)
- Couchbase → [`skills/shared/connectors/couchbase.md`](connectors/couchbase.md)
- Coupa → [`skills/shared/connectors/coupa.md`](connectors/coupa.md)
- Crystal Ball → [`skills/shared/connectors/crystalball.md`](connectors/crystalball.md)
- Databricks → [`skills/shared/connectors/databricks.md`](connectors/databricks.md)
- DocuSign → [`skills/shared/connectors/docusign.md`](connectors/docusign.md)
- Dropbox → [`skills/shared/connectors/dropbox.md`](connectors/dropbox.md)
- Eventbrite → [`skills/shared/connectors/eventbrite.md`](connectors/eventbrite.md)
- Expensify → [`skills/shared/connectors/expensify.md`](connectors/expensify.md)
- Factorial HR → [`skills/shared/connectors/factorialhr.md`](connectors/factorialhr.md)
- FileNet → [`skills/shared/connectors/filenet.md`](connectors/filenet.md)
- Freshservice → [`skills/shared/connectors/freshservice.md`](connectors/freshservice.md)
- Front → [`skills/shared/connectors/front.md`](connectors/front.md)
- GitHub → [`skills/shared/connectors/github.md`](connectors/github.md)
- GitLab → [`skills/shared/connectors/gitlab.md`](connectors/gitlab.md)
- Gmail → [`skills/shared/connectors/gmail.md`](connectors/gmail.md)
- Google Analytics → [`skills/shared/connectors/googleanalytics.md`](connectors/googleanalytics.md)
- Google BigQuery → [`skills/shared/connectors/googlebigquery.md`](connectors/googlebigquery.md)
- Google Calendar → [`skills/shared/connectors/googlecalendar.md`](connectors/googlecalendar.md)
- Google Chat → [`skills/shared/connectors/googlechat.md`](connectors/googlechat.md)
- Google Cloud Storage → [`skills/shared/connectors/google-cloud-storage.md`](connectors/google-cloud-storage.md)
- Google Contacts → [`skills/shared/connectors/googlecontacts.md`](connectors/googlecontacts.md)
- Google Drive → [`skills/shared/connectors/googledrive.md`](connectors/googledrive.md)
- Google Gemini → [`skills/shared/connectors/googlegemini.md`](connectors/googlegemini.md)
- Google Groups → [`skills/shared/connectors/googlegroups.md`](connectors/googlegroups.md)
- Google PubSub → [`skills/shared/connectors/googlepubsub.md`](connectors/googlepubsub.md)
- Google Sheets → [`skills/shared/connectors/googlesheet.md`](connectors/googlesheet.md)
- Google Tasks → [`skills/shared/connectors/googletasks.md`](connectors/googletasks.md)
- Google Translate → [`skills/shared/connectors/googletranslate.md`](connectors/googletranslate.md)
- Google Universal Analytics → [`skills/shared/connectors/googleuniversalanalytics.md`](connectors/googleuniversalanalytics.md)
- Greenhouse → [`skills/shared/connectors/greenhouse.md`](connectors/greenhouse.md)
- HashiCorp Vault → [`skills/shared/connectors/hashicorpvault.md`](connectors/hashicorpvault.md)
- HubSpot Marketing → [`skills/shared/connectors/hubspotmarketing.md`](connectors/hubspotmarketing.md)
- Hunter → [`skills/shared/connectors/hunter.md`](connectors/hunter.md)
- IBM Aspera → [`skills/shared/connectors/ibmaspera.md`](connectors/ibmaspera.md)
- IBM Cloudant → [`skills/shared/connectors/ibm-cloudant.md`](connectors/ibm-cloudant.md)
- IBM Cloud Object Storage S3 → [`skills/shared/connectors/ibmcoss3.md`](connectors/ibmcoss3.md)
- IBM Engineering Workflow Management → [`skills/shared/connectors/ibmewm.md`](connectors/ibmewm.md)
- IBM Food Trust → [`skills/shared/connectors/ift.md`](connectors/ift.md)
- IBM OpenPages → [`skills/shared/connectors/ibmopenpages.md`](connectors/ibmopenpages.md)
- IBM Sterling Intelligent Promising → [`skills/shared/connectors/ibmsterlingiv.md`](connectors/ibmsterlingiv.md)
- IBM Targetprocess → [`skills/shared/connectors/apptiotargetprocess.md`](connectors/apptiotargetprocess.md)
- IBM TWC → [`skills/shared/connectors/ibmtwc.md`](connectors/ibmtwc.md)
- Infobip → [`skills/shared/connectors/infobip.md`](connectors/infobip.md)
- Insightly → [`skills/shared/connectors/insightly.md`](connectors/insightly.md)
- Jenkins → [`skills/shared/connectors/jenkins.md`](connectors/jenkins.md)
- Jira → [`skills/shared/connectors/jira.md`](connectors/jira.md)
- Kronos → [`skills/shared/connectors/kronos.md`](connectors/kronos.md)
- LDAP → [`skills/shared/connectors/ldap.md`](connectors/ldap.md)
- Magento → [`skills/shared/connectors/magento.md`](connectors/magento.md)
- Mailchimp → [`skills/shared/connectors/mailchimp.md`](connectors/mailchimp.md)
- Marketo → [`skills/shared/connectors/marketo.md`](connectors/marketo.md)
- Maximo → [`skills/shared/connectors/maximo.md`](connectors/maximo.md)
- Microsoft Active Directory → [`skills/shared/connectors/msad.md`](connectors/msad.md)
- Microsoft Azure Blob Storage → [`skills/shared/connectors/microsoft-azure-blob-storage.md`](connectors/microsoft-azure-blob-storage.md)
- Microsoft Dynamics CRM REST → [`skills/shared/connectors/msdynamicscrmrest.md`](connectors/msdynamicscrmrest.md)
- Microsoft Dynamics F&O → [`skills/shared/connectors/msdynamicsfando.md`](connectors/msdynamicsfando.md)
- Microsoft Excel → [`skills/shared/connectors/msexcel.md`](connectors/msexcel.md)
- Microsoft Excel Online → [`skills/shared/connectors/microsoft-excel-online.md`](connectors/microsoft-excel-online.md)
- Microsoft Exchange → [`skills/shared/connectors/msexchange.md`](connectors/msexchange.md)
- Microsoft OneDrive → [`skills/shared/connectors/msonedrive.md`](connectors/msonedrive.md)
- Microsoft OneNote → [`skills/shared/connectors/msonenote.md`](connectors/msonenote.md)
- Microsoft Power BI → [`skills/shared/connectors/mspowerbi.md`](connectors/mspowerbi.md)
- Microsoft SharePoint → [`skills/shared/connectors/microsoft-sharepoint.md`](connectors/microsoft-sharepoint.md)
- Microsoft SharePoint (mssharepoint) → [`skills/shared/connectors/mssharepoint.md`](connectors/mssharepoint.md)
- Microsoft Teams → [`skills/shared/connectors/msteams.md`](connectors/msteams.md)
- Microsoft To Do → [`skills/shared/connectors/mstodo.md`](connectors/mstodo.md)
- Milvus → [`skills/shared/connectors/milvus.md`](connectors/milvus.md)
- Monday.com → [`skills/shared/connectors/mondaydotcom.md`](connectors/mondaydotcom.md)
- Oracle EBS → [`skills/shared/connectors/oracleebs.md`](connectors/oracleebs.md)
- Oracle HCM → [`skills/shared/connectors/oraclehcm.md`](connectors/oraclehcm.md)
- Pinecone DB → [`skills/shared/connectors/pineconedb.md`](connectors/pineconedb.md)
- Planning Analytics → [`skills/shared/connectors/planninganalytics.md`](connectors/planninganalytics.md)
- Redis → [`skills/shared/connectors/redis.md`](connectors/redis.md)
- Redis Cache → [`skills/shared/connectors/rediscache.md`](connectors/rediscache.md)
- Salesforce → [`skills/shared/connectors/salesforce.md`](connectors/salesforce.md)
- Salesforce AE → [`skills/shared/connectors/salesforceae.md`](connectors/salesforceae.md)
- Salesforce Marketing Cloud → [`skills/shared/connectors/salesforcemc.md`](connectors/salesforcemc.md)
- Salesloft → [`skills/shared/connectors/salesloft.md`](connectors/salesloft.md)
- SAP Ariba → [`skills/shared/connectors/sapariba.md`](connectors/sapariba.md)
- SAP Commerce Cloud → [`skills/shared/connectors/sapcommercecloud.md`](connectors/sapcommercecloud.md)
- SAP S/4HANA → [`skills/shared/connectors/saps4hana.md`](connectors/saps4hana.md)
- SAP SuccessFactors → [`skills/shared/connectors/sapsuccessfactors.md`](connectors/sapsuccessfactors.md)
- ServiceNow → [`skills/shared/connectors/service-now.md`](connectors/service-now.md)
- ServiceNow (servicenow) → [`skills/shared/connectors/servicenow.md`](connectors/servicenow.md)
- Salesforce Commerce Cloud Data → [`skills/shared/connectors/sfcommerceclouddata.md`](connectors/sfcommerceclouddata.md)
- Shopify → [`skills/shared/connectors/shopify.md`](connectors/shopify.md)
- Slack → [`skills/shared/connectors/slack.md`](connectors/slack.md)
- Snowflake → [`skills/shared/connectors/snowflake.md`](connectors/snowflake.md)
- Splunk → [`skills/shared/connectors/splunk.md`](connectors/splunk.md)
- Square → [`skills/shared/connectors/square.md`](connectors/square.md)
- SurveyMonkey → [`skills/shared/connectors/surveymonkey.md`](connectors/surveymonkey.md)
- Toggl Track → [`skills/shared/connectors/toggltrack.md`](connectors/toggltrack.md)
- Trello → [`skills/shared/connectors/trello.md`](connectors/trello.md)
- Twilio → [`skills/shared/connectors/twilio.md`](connectors/twilio.md)
- Vespa → [`skills/shared/connectors/vespa.md`](connectors/vespa.md)
- Watson Discovery → [`skills/shared/connectors/watsondiscovery.md`](connectors/watsondiscovery.md)
- WordPress → [`skills/shared/connectors/wordpress.md`](connectors/wordpress.md)
- Workday → [`skills/shared/connectors/workday.md`](connectors/workday.md)
- Wrike → [`skills/shared/connectors/wrike.md`](connectors/wrike.md)
- Wufoo → [`skills/shared/connectors/wufoo.md`](connectors/wufoo.md)
- Yammer → [`skills/shared/connectors/yammer.md`](connectors/yammer.md)
- Yapily → [`skills/shared/connectors/yapily.md`](connectors/yapily.md)
- Zendesk Service → [`skills/shared/connectors/zendeskservice.md`](connectors/zendeskservice.md)
- Zoho Books → [`skills/shared/connectors/zohobooks.md`](connectors/zohobooks.md)
- Zoho CRM → [`skills/shared/connectors/zohocrm.md`](connectors/zohocrm.md)
- Zoho Inventory → [`skills/shared/connectors/zohoinventory.md`](connectors/zohoinventory.md)
- Zoho Recruit → [`skills/shared/connectors/zohorecruit.md`](connectors/zohorecruit.md)
- z/OS Connect → [`skills/shared/connectors/zosconnect.md`](connectors/zosconnect.md)

