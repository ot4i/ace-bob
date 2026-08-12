# Roadmap

*Generalised restructure of the skill*
 * Restructure of ace-bob skill: [https://github.com/ot4i/ace-bob/pull/1]
 * Complete restructuring clean-up: [https://github.com/ot4i/ace-bob/pull/8]

*Add required updates to make the basics for all Discovery Connectors work*
 * Add Udita DocuSign contribution to fit restructuring: [https://github.com/ot4i/ace-bob/pull/3]
 * Add Amazon discovery connectors: [https://github.com/ot4i/ace-bob/pull/4]
 * Add discovery connectors from anaplan to cmis: [https://github.com/ot4i/ace-bob/pull/5]
 * Add discovery connectors from confluence to front: [https://github.com/ot4i/ace-bob/pull/6]
 * Add discovery connectors gmail and google connectors: [https://github.com/ot4i/ace-bob/pull/7]
 * Add discovery connectors from greenhouse to ibmzosconnect: [https://github.com/ot4i/ace-bob/pull/10]
 * Add discovery connectors from infobip to marketo:  [https://github.com/ot4i/ace-bob/pull/13]
 * Add Microsoft discovery connectors:  [https://github.com/ot4i/ace-bob/pull/14]
 * Add discovery connectors from milvus to salesforce: TO DO
 * Add discovery connectors from salesloft to twilio:  [https://github.com/ot4i/ace-bob/pull/15]
 * Add discovery connectors from UKG to zohorecruit:  [https://github.com/ot4i/ace-bob/pull/16]

*Add improvements around the structure of the message flow file*
 * Add direct guidance about subflow nodes and their correct xmi:type including library qualified references: TO DO
 * Add direct guidance about the composition element wrapper: TO DO
 * Add direct guidance about node terminal naming (issue around capitalisation of in and out terminals?): TO DO
 * Add direct guidance about eflow namespace URI: TO DO
 * Add direct guidance about eSuperTypes URI: TO DO
 * Add direct guidance about platform specific paths for Windows / xLinux / MacOS: TO DO
 * Embed an example .msgflow to avoid recurrent behaviour of seeking ping_mq.msgflow: [https://github.com/ot4i/ace-bob/pull/9]
 * Add direct guidance about nodeLayoutStyle of RECTANGLE: TO DO
 * Add direct guidance for REST node families
 * Add direct guidance for SOAP node families
 * Add direct guidance for TCPIP node families

*Add specifics to create well-structured REST APIs*
 * Add examples and rules for Swagger and OpenAPI and operation to subflow mapping: [https://github.com/ot4i/ace-bob/pull/9]

*Add specifics to support shared library and static library projects* 
 * Add rules for metadata needed for libraries including library.descriptor and .project:  [https://github.com/ot4i/ace-bob/pull/11]
 * Add rules for linking one project to another through project references: TO DO

*Add improvements for ESQL handling*
 * Add rules for BROKER SCHEMA to match with subdirectory locations of ESQL files: [https://github.com/ot4i/ace-bob/pull/12]
 * Add rules for Compute and Filter module properties: TO DO
 * Add rules about usage of templates for CopyMessageHeaders() and CopyEntireMessage(): TO DO
 * Provide guidance on when to use SHARED and EXTERNAL variables: TO DO
 * Provide guidance on using COALESCE() function when reading potential nulls: TO DO
 * Provide guidance on using PROPAGATE and RETURN FALSE/TRUE depending on desire to suppress default propagation: TO DO
 * Provide guidance on standard practice for using Environment.Variables: TO DO
 * Provide guidance for message flow naming conventions: TO DO
 * Provide guidance to avoid unconnected nodes (incorporating allowance for Input nodes and Label nodes): TO DO

*Add improvements for Map handling*
 * Add dedicated shared guidance for Maps and `.map` file generation.
