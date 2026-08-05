# ACE Toolkit Projects: Application Projects, REST API Projects and Integration Service Projects

## Purpose
This document defines the required structure for IBM App Connect Enterprise (ACE) Toolkit projects.
There are three types of Toolkit projects which can be used to hold message flows: Application Projects, REST API Projects and Integration Service Projects

## When to Create an Application Project
- If the user asks for a message flow, ESQL file, map, or related ACE Toolkit artifact and does not specify an existing Application project, create a new Application project.
- If the user does not provide a project name, use the message flow name without the `.msgflow` extension.

## Required Files in Application Projects
An ACE Toolkit Application project must contain:
- a `.project` file in the project root
- a `.settings` directory
- a `.settings/org.eclipse.core.resources.prefs` file
- an `application.descriptor` file in the project root

**Every one of these files must be created as explicit file output.** Do not describe the project structure in prose and omit any of them. If a file is listed here and not present in the output, the project is incomplete.

## `.project` File Requirements for an Application project

**Use the following complete `.project` file verbatim.** Replace `<ProjectName>` with the actual project folder name. Do not add, remove, or modify any `<nature>` entries — the file must contain exactly the two natures shown and no others.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<projectDescription>
	<name><ProjectName></name>
	<comment></comment>
	<projects>
	</projects>
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
	<natures>
		<nature>com.ibm.etools.msgbroker.tooling.applicationNature</nature>
		<nature>com.ibm.etools.msgbroker.tooling.messageBrokerProjectNature</nature>
	</natures>
</projectDescription>
```

## `.settings` Requirements for an Application project
The `.settings/org.eclipse.core.resources.prefs` file must contain:

```properties
eclipse.preferences.version=1
encoding/<project>=UTF-8
```

**`<project>` is a placeholder — replace it with the actual project folder name.** For example, if the project is named `HTTPEchoApp`, the file must contain:

```properties
eclipse.preferences.version=1
encoding/HTTPEchoApp=UTF-8
```

Omitting this substitution causes the Toolkit warning: `Project '<name>' has no explicit encoding set`.

## `application.descriptor` Requirements for an Application project
The `application.descriptor` file must exist in the project root and must use the following exact content — do not add `<reference>` entries:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ns2:appDescriptor xmlns="http://com.ibm.etools.mft.descriptor.base" xmlns:ns2="http://com.ibm.etools.mft.descriptor.app">
<references/>
</ns2:appDescriptor>
```

## When to Create a REST API Project
- If the user asks for ACE to expose a REST API interface, or if the user provides a Swagger document or Open API document when describing the input data structure for a message flow, then create a new REST API project.
- In ACE, a REST API is a specialized application that can be called by HTTP clients. 
- The REST API project is structured to contain specific files that follow a particular pattern.
- Each REST API project must contain either an OpenAPI 3.0 document (named openapi.json) OR a Swagger 2.0 document (named swagger.json)
- If the user does not express a preference you should use an OpenAPI 3.0 document named openapi.json in preference to a Swagger 2.0 document.
- If using an OpenAPI 3.0 document and you are not told otherwise then by default within the info object, the title and description should match the name of the REST API project.
- If using an OpenAPI 3.0 document and you are not told otherwise then by default within the info object, the version should be set to 1.0.0
- If using an OpenAPI 3.0 document and you are not told otherwise then by default within the info object, the version should be set to 1.0.0
- If using an OpenAPI 3.0 document and you are not told otherwise then by default the url property shoul dbe based on a lower case version of the REST API project name and its version. For example, MyRESTAPI at version 1.0.0 would have a basePath of "/myrestapi/v1"
- ACE places some restrictions on the Open API 3.0 documents that can be used to create a REST API that are documented here: https://www.ibm.com/docs/en/app-connect/13.0.x?topic=apis-restrictions-openapi-30-documents
- If using a Swagger 2.0 document and you are not told otherwise then by default the title and description should match the name of the REST API project.
- If using a Swagger 2.0 document and you are not told otherwise then by default the version should be set to 1.0.0
- If using a Swagger 2.0 document and you are not told otherwise then by default the basePath should be based on a lower case version of the REST API project name and its version. For example, MyRESTAPI at version 1.0.0 would have a basePath of "/myrestapi/v1"
- ACE places some restrictions on the Swagger documents that can be used to create a REST API that are documented here: https://www.ibm.com/docs/en/app-connect/13.0.x?topic=apis-restrictions-swagger-documents

## Required Files in REST API Projects
An ACE Toolkit REST API project must contain:
- a `.project` file in the project root
- a `restapi.descriptor` file in the project root
- an `openapi.json` file in the project root (or alternatively if requested a `swagger.json` )
- a `gen/<RESTAPIProjectName>.msgflow` file where <RESTAPIProjectName> is the name of the REST API Project
- a `<operationId>.subflow` file for each operation defined in the REST API  (operations are either defined in openapi.json or swagger.json). The name of the subflow file should match the name of the operationId and the file extension should be .subflow

**Every one of these files must be created as explicit file output.** Do not describe the project structure in prose and omit any of them. If a file is listed here and not present in the output, the project is incomplete.

## `.project` File Requirements for a REST API project

**Use the following complete `.project` file verbatim.** Replace `<ProjectName>` with the actual project folder name. Do not add, remove, or modify any `<nature>` entries — the file must contain exactly the two natures shown and no others.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<projectDescription>
	<name><ProjectName></name>
	<comment></comment>
	<projects>
	</projects>
	<buildSpec>
		<buildCommand>
			<name>com.ibm.etools.mft.restapi.ui.restApiBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>com.ibm.etools.mft.json.builder.JSONBuilder</name>
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
	</buildSpec>
	<natures>
		<nature>com.ibm.etools.mft.restapi.ui.Nature</nature>
		<nature>com.ibm.etools.msgbroker.tooling.messageBrokerProjectNature</nature>
		<nature>com.ibm.etools.msgbroker.tooling.applicationNature</nature>
	</natures>
</projectDescription>
```

## `restapi.descriptor` Requirements for a REST API project
** Use the following complete `restapi.descriptor` in the project root ** Replace `<ProjectName>` with the actual project folder name.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ns2:restapiDescriptor xmlns="http://com.ibm.etools.mft.descriptor.base" xmlns:ns2="http://com.ibm.etools.mft.descriptor.restapi" definitionType="openapi_3" definitionFile="openapi.json" implementation="gen/<ProjectName>.msgflow" https="false" definitionWithExtRef="false" faultFormat="JSON">
    <ns2:operations/>
    <ns2:errorHandlers/>
</ns2:restapiDescriptor>
```

## Output Note
If a new project is created (whether it is an Application or a REST API), include this note in the final response:

"If you are working in the ACE Toolkit then to see the results and do further work with the generated project in the Application Development view, use the menu option File > Import > Existing Projects into Workspace."

## Version Notes
For version-specific schema or project structure differences, refer to `skills/shared/ace-versions.md`.
