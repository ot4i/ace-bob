# ACE Version References

## Purpose
This document centralizes version-specific IBM App Connect Enterprise (ACE) references used by the ACE Bob skills.

## When to use
Use this document whenever a task depends on schema validation, project structure differences, or other version-specific ACE behavior.

## Default version behavior
- If the user explicitly states an ACE version, use that version.
- If the user does not state an ACE version and the task depends on schema validation or version-specific file structure, ask the user which ACE version they are using.
- If the task does not depend on version-specific differences, proceed using the repository's documented default assumptions and clearly state those assumptions in the response.

## Supported version references
The current repository content was originally authored with ACE 13-era schema paths in mind. Version-specific references should be maintained here rather than embedded throughout other files.

## Schema locations
### Message Flow schema
Example ACE 13 path:
`C:\Program Files\IBM\ACE\13.0.7.0\common\schemas\MessageFlow\MessageFlow.xsd`

### Policy schema
Example ACE 13 path:
`C:\Program Files\IBM\ACE\13.0.7.0\common\schemas\Policy\Policy.xsd`

## Rules
- Do not hard-code ACE schema locations in multiple documents when a reference to this file is sufficient.
- When validating node `xmi:type` values, use the Message Flow schema applicable to the user's ACE version.
- When validating policy XML content, use the Policy schema applicable to the user's ACE version.

## Related files
- [`skills/shared/message-flow-rules.md`](message-flow-rules.md)
- [`skills/shared/node-types.md`](node-types.md)
- [`skills/shared/policy-projects.md`](policy-projects.md)

## Maintenance notes
- Add new ACE versions here as they are validated.
- If a later ACE version changes schema locations or node type names, document those differences here.
