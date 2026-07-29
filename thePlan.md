Stabilize top-level entry points

Update README.md to describe the current repo purpose, list all active skills, and reduce migration-era wording.
Update SKILL.md to act as a clear compatibility/redirect entry point to the canonical skills under skills/.
Standardize active skill files

Review and normalize the structure and wording of:
skills/ace-message-flow/SKILL.md
skills/ace-connector-flows/SKILL.md
skills/ace-project-setup/SKILL.md
skills/ace-esql/SKILL.md
skills/ace-java-compute/SKILL.md
Ensure each skill has a consistent format for purpose, required reading order, critical rules, and output requirements.
Validate and refine shared guidance

Compare skills/shared/node-types.md against the node catalog in originalSKILL.md to catch missing entries, malformed migrated lines, and incorrect copied text.
Keep version-specific references centralized in skills/shared/ace-versions.md.
Reduce overlap across shared docs by keeping each file focused on one responsibility.
Standardize connector guidance

Review the migrated connector docs under skills/shared/connectors/ for consistent layout and naming.
Ensure skills/shared/connector-index.md matches the actual connector files and clearly indicates it is the index of migrated canonical connector guidance.
Standardize legacy compatibility stubs

Review the legacy root connector files such as AmazonS3.md, GitHub.md, and the other root connector markdown files.
Ensure each one clearly states it is legacy, should not be updated, and points to the canonical file under skills/shared/connectors/.
Refresh backlog/status docs

Update backlog/known-issues.md so it reflects the actual remaining gaps after the migration work.
Update backlog/roadmap.md to track only real remaining work rather than already completed restructuring.
Validation pass

Re-read changed files for formatting and consistency.
Run a repo diff check to confirm the changes are limited to the planned documentation restructure and cleanup.