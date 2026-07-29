# ACE Policy Projects

## Purpose
This document defines the required structure for IBM App Connect Enterprise (ACE) Policy projects.

## When to use
Use this document when a connector node requires a policy project or when reviewing existing ACE Policy project scaffolding.

## When to create a Policy project
- Create a Policy project when a connector node requires a policy and the user has not identified an existing suitable Policy project.
- Policy files must be created in a Policy project, not in an Application project.

## Required project files
An ACE Policy project must contain:
- a `.project` file in the project root
- a `.settings` directory
- a `.settings/org.eclipse.core.resources.prefs` file
- a `policy.descriptor` file in the project root

## `.project` requirements
ACE Policy projects **MUST** contain the following natures section:

```xml
<natures>
  <nature>com.ibm.etools.mft.policy.ui.Nature</nature>
</natures>
```

ACE Policy projects **MUST** contain the following buildSpec section:

```xml
<buildSpec>
  <buildCommand>
    <name>com.ibm.etools.mft.policy.ui.policybuilder</name>
    <arguments>
    </arguments>
  </buildCommand>
</buildSpec>
```

## `.settings` requirements
The `.settings/org.eclipse.core.resources.prefs` file must contain:

```properties
eclipse.preferences.version=1
encoding/<project>=UTF-8
```

## `policy.descriptor` requirements
The `policy.descriptor` file must exist in the project root and use the validated ACE structure.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<ns2:policyProjectDescriptor xmlns="http://com.ibm.etools.mft.descriptor.base" xmlns:ns2="http://com.ibm.etools.mft.descriptor.policyProject">
  <references/>
</ns2:policyProjectDescriptor>
```

## Policy file placement
- Policy files should be created in the root of the Policy project.
- If the user does not specify a policy file name, derive one from the node type and a numeric suffix.

## Validation
- Validate policy XML structure using the Policy schema for the applicable ACE version.
- For schema locations, refer to [`skills/shared/ace-versions.md`](ace-versions.md).

## Related files
- [`skills/shared/ace-versions.md`](ace-versions.md)
- [`skills/shared/connector-index.md`](connector-index.md)
