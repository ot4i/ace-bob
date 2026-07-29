# ACE Toolkit Application Projects

## Purpose
This document defines the required structure for IBM App Connect Enterprise (ACE) Toolkit Application projects.

## When to Create an Application Project
- If the user asks for a message flow, ESQL file, map, or related ACE Toolkit artifact and does not specify an existing Application project, create a new Application project.
- If the user does not provide a project name, use the message flow name without the `.msgflow` extension.

## Required Project Files
An ACE Toolkit Application project must contain:
- a `.project` file in the project root
- a `.settings` directory
- a `.settings/org.eclipse.core.resources.prefs` file
- an `application.descriptor` file in the project root

**Every one of these files must be created as explicit file output.** Do not describe the project structure in prose and omit any of them. If a file is listed here and not present in the output, the project is incomplete.

## `.project` Requirements

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

## `.settings` Requirements
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

## `application.descriptor` Requirements
The `application.descriptor` file must exist in the project root and must use the following exact content — do not add `<reference>` entries:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ns2:appDescriptor xmlns="http://com.ibm.etools.mft.descriptor.base" xmlns:ns2="http://com.ibm.etools.mft.descriptor.app">
<references/>
</ns2:appDescriptor>
```

## Output Note
If a new Application project is created, include this note in the final response:

"If you are working in the ACE Toolkit then to see the results and do further work with the generated project in the Application Development view, use the menu option File > Import > Existing Projects into Workspace."

## Version Notes
For version-specific schema or project structure differences, refer to `skills/shared/ace-versions.md`.
