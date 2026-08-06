# HashiCorp Vault

## Purpose
Connector-specific rules for HashiCorp Vault Request nodes.

## When to use
Use this document when the requested ACE flow includes a HashiCorp Vault Request node.

## Prerequisites
Before using this document, read:
- [`skills/shared/message-flow-rules.md`](../message-flow-rules.md)
- [`skills/shared/node-types.md`](../node-types.md)
- [`skills/shared/policy-projects.md`](../policy-projects.md)
- [`skills/shared/ace-versions.md`](../ace-versions.md)

## Supported node types
- HashiCorp Vault Request node

## Required node attributes
- `xmi:type` must use the namespace prefix of `ComIbmApplicationConnectorRequest_hashicorpvault.msgnode`
- `applicationConnectorType="hashicorpvault"`
- a `schemaPrefix` attribute is required
- a `policyUrl` attribute is required

## Schema file requirements
For HashiCorp Vault Request nodes:
- create an empty request schema JSON file under the `gen` directory
- create an empty response schema JSON file under the `gen` directory
- use the schema prefix naming convention documented in the legacy connector guidance

## Allowed operations
Operations are organised by secrets engine. The `action` value is the operation key from the engine's `operations.json` file. The `businessObject` value is the engine name as it appears in discovery.

### KV v1 (`kv1`)
- `displayName="Retrieve secret from KV store"` `action="kv-v1-read"` `businessObject="kv1"`
- `displayName="Create or update secret to KV store"` `action="kv-v1-write"` `businessObject="kv1"`
- `displayName="Delete secret from KV store"` `action="kv-v1-delete"` `businessObject="kv1"`
- `displayName="Retrieve secrets in KV store"` `action="kv-v1-list"` `businessObject="kv1"`

### KV v2 (`kv2`)
- `displayName="Retrieve KV v2 configuration"` `action="kv-v2-read-configuration"` `businessObject="kv2"`
- `displayName="Configure KV v2 engine"` `action="kv-v2-configure"` `businessObject="kv2"`
- `displayName="Retrieve secret from KV v2"` `action="kv-v2-read"` `businessObject="kv2"`
- `displayName="Create or update secret to KV v2"` `action="kv-v2-write"` `businessObject="kv2"`
- `displayName="Patch secret in KV v2"` `action="kv-v2-patch"` `businessObject="kv2"`
- `displayName="Delete latest version"` `action="kv-v2-delete"` `businessObject="kv2"`
- `displayName="Delete specific versions"` `action="kv-v2-delete-versions"` `businessObject="kv2"`
- `displayName="Destroy specific versions"` `action="kv-v2-destroy-versions"` `businessObject="kv2"`
- `displayName="Retrieve secret metadata"` `action="kv-v2-read-metadata"` `businessObject="kv2"`
- `displayName="Create or update secret metadata"` `action="kv-v2-write-metadata"` `businessObject="kv2"`
- `displayName="Patch secret metadata"` `action="kv-v2-patch-metadata-path"` `businessObject="kv2"`
- `displayName="Delete metadata and all versions"` `action="kv-v2-delete-metadata-and-all-versions"` `businessObject="kv2"`
- `displayName="Retrieve secrets in KV v2"` `action="kv-v2-list"` `businessObject="kv2"`
- `displayName="Retrieve secret subkeys"` `action="kv-v2-read-subkeys"` `businessObject="kv2"`
- `displayName="Undelete specific versions"` `action="kv-v2-undelete-versions"` `businessObject="kv2"`

### Cubbyhole (`cubbyhole`)
- `displayName="Retrieve secret from Cubbyhole"` `action="cubbyhole-read"` `businessObject="cubbyhole"`
- `displayName="Create or update secret to Cubbyhole"` `action="cubbyhole-write"` `businessObject="cubbyhole"`
- `displayName="Delete secret from Cubbyhole"` `action="cubbyhole-delete"` `businessObject="cubbyhole"`
- `displayName="Retrieve secrets in Cubbyhole"` `action="cubbyhole-list"` `businessObject="cubbyhole"`

### Transit (`transit`)
- `displayName="Encrypt data"` `action="transit-encrypt"` `businessObject="transit"`
- `displayName="Decrypt data"` `action="transit-decrypt"` `businessObject="transit"`
- `displayName="Rewrap encrypted data"` `action="transit-rewrap"` `businessObject="transit"`
- `displayName="Create encryption key"` `action="transit-create-key"` `businessObject="transit"`
- `displayName="Retrieve encryption key"` `action="transit-read-key"` `businessObject="transit"`
- `displayName="Retrieve encryption keys"` `action="transit-list-keys"` `businessObject="transit"`
- `displayName="Delete encryption key"` `action="transit-delete-key"` `businessObject="transit"`
- `displayName="Configure key"` `action="transit-configure-key"` `businessObject="transit"`
- `displayName="Rotate encryption key"` `action="transit-rotate-key"` `businessObject="transit"`
- `displayName="Import key"` `action="transit-import-key"` `businessObject="transit"`
- `displayName="Import key version"` `action="transit-import-key-version"` `businessObject="transit"`
- `displayName="Export encryption key"` `action="transit-export-key"` `businessObject="transit"`
- `displayName="Export key version"` `action="transit-export-key-version"` `businessObject="transit"`
- `displayName="Backup encryption key"` `action="transit-back-up-key"` `businessObject="transit"`
- `displayName="Restore encryption key"` `action="transit-restore-key"` `businessObject="transit"`
- `displayName="Restore and rename key"` `action="transit-restore-and-rename-key"` `businessObject="transit"`
- `displayName="Trim key versions"` `action="transit-trim-key"` `businessObject="transit"`
- `displayName="Sign data"` `action="transit-sign"` `businessObject="transit"`
- `displayName="Sign data with algorithm"` `action="transit-sign-with-algorithm"` `businessObject="transit"`
- `displayName="Verify signature"` `action="transit-verify"` `businessObject="transit"`
- `displayName="Verify signature with algorithm"` `action="transit-verify-with-algorithm"` `businessObject="transit"`
- `displayName="Hash data"` `action="transit-hash"` `businessObject="transit"`
- `displayName="Hash data with algorithm"` `action="transit-hash-with-algorithm"` `businessObject="transit"`
- `displayName="Generate HMAC"` `action="transit-generate-hmac"` `businessObject="transit"`
- `displayName="Generate HMAC with algorithm"` `action="transit-generate-hmac-with-algorithm"` `businessObject="transit"`
- `displayName="Generate CMAC"` `action="transit-generate-cmac"` `businessObject="transit"`
- `displayName="Generate CMAC with MAC length"` `action="transit-generate-cmac-with-mac-length"` `businessObject="transit"`
- `displayName="Generate a data key"` `action="transit-generate-data-key"` `businessObject="transit"`
- `displayName="Generate multiple data keys"` `action="transit-generate-multiple-data-keys"` `businessObject="transit"`
- `displayName="Generate derived keys"` `action="transit-generate-derivedkeys"` `businessObject="transit"`
- `displayName="Generate random bytes"` `action="transit-generate-random"` `businessObject="transit"`
- `displayName="Generate random with source"` `action="transit-generate-random-with-source"` `businessObject="transit"`
- `displayName="Generate random with source and bytes"` `action="transit-generate-random-with-source-and-bytes"` `businessObject="transit"`
- `displayName="Generate random with bytes"` `action="transit-generate-random-with-bytes"` `businessObject="transit"`
- `displayName="Retrieve cache configuration"` `action="transit-read-cache-configuration"` `businessObject="transit"`
- `displayName="Configure cache"` `action="transit-configure-cache"` `businessObject="transit"`
- `displayName="Retrieve keys configuration"` `action="transit-read-keys-configuration"` `businessObject="transit"`
- `displayName="Configure keys"` `action="transit-configure-keys"` `businessObject="transit"`
- `displayName="Securely export key"` `action="transit-byok-key"` `businessObject="transit"`
- `displayName="Securely export key version"` `action="transit-byok-key-version"` `businessObject="transit"`
- `displayName="Generate CSR for key"` `action="transit-generate-csr-for-key"` `businessObject="transit"`
- `displayName="Set certificate for key"` `action="transit-set-certificate-for-key"` `businessObject="transit"`
- `displayName="Retrieve wrapping key"` `action="transit-read-wrapping-key"` `businessObject="transit"`

### TOTP (`totp`)
- `displayName="Generate TOTP code"` `action="totp-generate-code"` `businessObject="totp"`
- `displayName="Validate TOTP code"` `action="totp-validate-code"` `businessObject="totp"`
- `displayName="Create or update TOTP key"` `action="totp-create-key"` `businessObject="totp"`
- `displayName="Retrieve TOTP key"` `action="totp-read-key"` `businessObject="totp"`
- `displayName="Retrieve TOTP keys"` `action="totp-list-keys"` `businessObject="totp"`
- `displayName="Delete TOTP key"` `action="totp-delete-key"` `businessObject="totp"`

### SSH (`ssh`)
- `displayName="Issue certificate"` `action="ssh-issue-certificate"` `businessObject="ssh"`
- `displayName="Sign certificate"` `action="ssh-sign-certificate"` `businessObject="ssh"`
- `displayName="Generate credentials"` `action="ssh-generate-credentials"` `businessObject="ssh"`
- `displayName="Create or update role"` `action="ssh-write-role"` `businessObject="ssh"`
- `displayName="Retrieve role"` `action="ssh-read-role"` `businessObject="ssh"`
- `displayName="Retrieve roles"` `action="ssh-list-roles"` `businessObject="ssh"`
- `displayName="Delete role"` `action="ssh-delete-role"` `businessObject="ssh"`
- `displayName="Retrieve roles by IP"` `action="ssh-list-roles-by-ip"` `businessObject="ssh"`
- `displayName="Retrieve public key"` `action="ssh-read-public-key"` `businessObject="ssh"`
- `displayName="Retrieve CA configuration"` `action="ssh-read-ca-configuration"` `businessObject="ssh"`
- `displayName="Configure CA"` `action="ssh-configure-ca"` `businessObject="ssh"`
- `displayName="Delete CA configuration"` `action="ssh-delete-ca-configuration"` `businessObject="ssh"`
- `displayName="Retrieve zero address configuration"` `action="ssh-read-zero-address-configuration"` `businessObject="ssh"`
- `displayName="Configure zero address"` `action="ssh-configure-zero-address"` `businessObject="ssh"`
- `displayName="Delete zero address configuration"` `action="ssh-delete-zero-address-configuration"` `businessObject="ssh"`
- `displayName="Verify OTP"` `action="ssh-verify-otp"` `businessObject="ssh"`
- `displayName="Tidy dynamic host keys"` `action="ssh-tidy-dynamic-host-keys"` `businessObject="ssh"`

### Database (`database`)
- `displayName="Configure database connection"` `action="database-configure-connection"` `businessObject="database"`
- `displayName="Retrieve database connection configuration"` `action="database-read-connection-configuration"` `businessObject="database"`
- `displayName="Retrieve database connections"` `action="database-list-connections"` `businessObject="database"`
- `displayName="Delete database connection"` `action="database-delete-connection-configuration"` `businessObject="database"`
- `displayName="Reset database connection"` `action="database-reset-connection"` `businessObject="database"`
- `displayName="Reload database plugin"` `action="database-reload-plugin"` `businessObject="database"`
- `displayName="Rotate root credentials"` `action="database-rotate-root-credentials"` `businessObject="database"`
- `displayName="Create or update database role"` `action="database-write-role"` `businessObject="database"`
- `displayName="Retrieve database role"` `action="database-read-role"` `businessObject="database"`
- `displayName="Retrieve database roles"` `action="database-list-roles"` `businessObject="database"`
- `displayName="Delete database role"` `action="database-delete-role"` `businessObject="database"`
- `displayName="Generate database credentials"` `action="database-generate-credentials"` `businessObject="database"`
- `displayName="Create or update static database role"` `action="database-write-static-role"` `businessObject="database"`
- `displayName="Retrieve static database role"` `action="database-read-static-role"` `businessObject="database"`
- `displayName="Retrieve static database roles"` `action="database-list-static-roles"` `businessObject="database"`
- `displayName="Delete static database role"` `action="database-delete-static-role"` `businessObject="database"`
- `displayName="Retrieve static role credentials"` `action="database-read-static-role-credentials"` `businessObject="database"`
- `displayName="Rotate static credentials"` `action="database-rotate-static-role-credentials"` `businessObject="database"`

### LDAP (`ldap`)
- `displayName="Retrieve LDAP configuration"` `action="ldap-read-configuration"` `businessObject="ldap"`
- `displayName="Configure LDAP"` `action="ldap-configure"` `businessObject="ldap"`
- `displayName="Delete LDAP configuration"` `action="ldap-delete-configuration"` `businessObject="ldap"`
- `displayName="Request dynamic role credentials"` `action="ldap-request-dynamic-role-credentials"` `businessObject="ldap"`
- `displayName="Retrieve dynamic roles"` `action="ldap-list-dynamic-roles"` `businessObject="ldap"`
- `displayName="Retrieve dynamic role"` `action="ldap-read-dynamic-role"` `businessObject="ldap"`
- `displayName="Create or update dynamic role"` `action="ldap-write-dynamic-role"` `businessObject="ldap"`
- `displayName="Delete dynamic role"` `action="ldap-delete-dynamic-role"` `businessObject="ldap"`
- `displayName="Retrieve static roles"` `action="ldap-list-static-roles"` `businessObject="ldap"`
- `displayName="Retrieve static role"` `action="ldap-read-static-role"` `businessObject="ldap"`
- `displayName="Create or update static role"` `action="ldap-write-static-role"` `businessObject="ldap"`
- `displayName="Delete static role"` `action="ldap-delete-static-role"` `businessObject="ldap"`
- `displayName="Request static role credentials"` `action="ldap-request-static-role-credentials"` `businessObject="ldap"`
- `displayName="Rotate static role credentials"` `action="ldap-rotate-static-role"` `businessObject="ldap"`
- `displayName="Rotate root credentials"` `action="ldap-rotate-root-credentials"` `businessObject="ldap"`
- `displayName="Retrieve library sets"` `action="ldap-library-list"` `businessObject="ldap"`
- `displayName="Retrieve library set"` `action="ldap-library-read"` `businessObject="ldap"`
- `displayName="Create or update library set"` `action="ldap-library-configure"` `businessObject="ldap"`
- `displayName="Delete library set"` `action="ldap-library-delete"` `businessObject="ldap"`
- `displayName="Check-in library account"` `action="ldap-library-check-in"` `businessObject="ldap"`
- `displayName="Check-out library account"` `action="ldap-library-check-out"` `businessObject="ldap"`
- `displayName="Force check-in library account"` `action="ldap-library-force-check-in"` `businessObject="ldap"`
- `displayName="Check library account status"` `action="ldap-library-check-status"` `businessObject="ldap"`
- `displayName="Retrieve library path"` `action="ldap-library-list-library-path"` `businessObject="ldap"`
- `displayName="Retrieve role path"` `action="ldap-list-role-path"` `businessObject="ldap"`
- `displayName="Retrieve static role path"` `action="ldap-list-static-role-path"` `businessObject="ldap"`
- `displayName="Retrieve migration status"` `action="ldap-read-migration"` `businessObject="ldap"`
- `displayName="Migrate LDAP"` `action="ldap-migrate"` `businessObject="ldap"`
- `displayName="Stop migration"` `action="ldap-stop-migration"` `businessObject="ldap"`

### KMIP (`kmip`)
- `displayName="Retrieve CA PEM"` `action="kmip-read-ca-pem"` `businessObject="kmip"`
- `displayName="Retrieve KMIP configuration"` `action="kmip-read-configuration"` `businessObject="kmip"`
- `displayName="Configure KMIP engine"` `action="kmip-configure"` `businessObject="kmip"`
- `displayName="Retrieve scopes"` `action="kmip-list-scopes"` `businessObject="kmip"`
- `displayName="Create scope"` `action="kmip-create-scope"` `businessObject="kmip"`
- `displayName="Delete scope"` `action="kmip-delete-scope"` `businessObject="kmip"`
- `displayName="Retrieve roles"` `action="kmip-list-roles"` `businessObject="kmip"`
- `displayName="Retrieve role"` `action="kmip-read-role"` `businessObject="kmip"`
- `displayName="Create or update role"` `action="kmip-write-role"` `businessObject="kmip"`
- `displayName="Delete role"` `action="kmip-delete-role"` `businessObject="kmip"`
- `displayName="Retrieve credential serial numbers"` `action="kmip-list-client-certificates"` `businessObject="kmip"`
- `displayName="Generate client certificate"` `action="kmip-generate-client-certificate"` `businessObject="kmip"`
- `displayName="Retrieve client certificate"` `action="kmip-retrieve-client-certificate"` `businessObject="kmip"`
- `displayName="Revoke client certificate"` `action="kmip-revoke-client-certificate"` `businessObject="kmip"`
- `displayName="Sign client certificate"` `action="kmip-sign-client-certificate-request"` `businessObject="kmip"`

### Key Management (`keymgmt`)
- `displayName="Retrieve managed keys"` `action="key-management-list-keys"` `businessObject="keymgmt"`
- `displayName="Retrieve managed key"` `action="key-management-read-key"` `businessObject="keymgmt"`
- `displayName="Update managed key"` `action="key-management-update-key"` `businessObject="keymgmt"`
- `displayName="Delete managed key"` `action="key-management-delete-key"` `businessObject="keymgmt"`
- `displayName="Rotate managed key"` `action="key-management-rotate-key"` `businessObject="keymgmt"`
- `displayName="Retrieve KMS providers"` `action="key-management-list-kms-providers"` `businessObject="keymgmt"`
- `displayName="Retrieve KMS provider"` `action="key-management-read-kms-provider"` `businessObject="keymgmt"`
- `displayName="Create or update KMS provider"` `action="key-management-write-kms-provider"` `businessObject="keymgmt"`
- `displayName="Delete KMS provider"` `action="key-management-delete-kms-provider"` `businessObject="keymgmt"`
- `displayName="Retrieve KMS providers for key"` `action="key-management-list-kms-providers-for-key"` `businessObject="keymgmt"`
- `displayName="Retrieve keys in KMS provider"` `action="key-management-list-keys-in-kms-provider"` `businessObject="keymgmt"`
- `displayName="Retrieve key in KMS provider"` `action="key-management-read-key-in-kms-provider"` `businessObject="keymgmt"`
- `displayName="Distribute key in KMS provider"` `action="key-management-distribute-key-in-kms-provider"` `businessObject="keymgmt"`
- `displayName="Delete key in KMS provider"` `action="key-management-delete-key-in-kms-provider"` `businessObject="keymgmt"`

### Transform (`transform`)
- `displayName="Encode data"` `action="transform-encode"` `businessObject="transform"`
- `displayName="Decode data"` `action="transform-decode"` `businessObject="transform"`
- `displayName="Decode data with format"` `action="transform-decode-with-format"` `businessObject="transform"`
- `displayName="Retrieve transformations"` `action="transform-list-transformations"` `businessObject="transform"`
- `displayName="Retrieve transformation"` `action="transform-read-transformation"` `businessObject="transform"`
- `displayName="Create or update transformation"` `action="transform-write-transformation"` `businessObject="transform"`
- `displayName="Delete transformation"` `action="transform-delete-transformation"` `businessObject="transform"`
- `displayName="Retrieve FPE transformations"` `action="transform-list-fpe-transformations"` `businessObject="transform"`
- `displayName="Retrieve FPE transformation"` `action="transform-read-fpe-transformation"` `businessObject="transform"`
- `displayName="Create or update FPE transformation"` `action="transform-write-fpe-transformation"` `businessObject="transform"`
- `displayName="Delete FPE transformation"` `action="transform-delete-fpe-transformation"` `businessObject="transform"`
- `displayName="Create FPE transformation with imported keys"` `action="transform-create-fpe-transformation-with-imported-keys"` `businessObject="transform"`
- `displayName="Retrieve masking transformations"` `action="transform-list-masking-transformations"` `businessObject="transform"`
- `displayName="Retrieve masking transformation"` `action="transform-read-masking-transformation"` `businessObject="transform"`
- `displayName="Create or update masking transformation"` `action="transform-write-masking-transformation"` `businessObject="transform"`
- `displayName="Delete masking transformation"` `action="transform-delete-masking-transformation"` `businessObject="transform"`
- `displayName="List tokenization transformations"` `action="transform-list-tokenization-transformations"` `businessObject="transform"`
- `displayName="Retrieve tokenization transformation"` `action="transform-read-tokenization-transformation"` `businessObject="transform"`
- `displayName="Create or update tokenization transformation"` `action="transform-write-tokenization-transformation"` `businessObject="transform"`
- `displayName="Delete tokenization transformation"` `action="transform-delete-tokenization-transformation"` `businessObject="transform"`
- `displayName="Create tokenization transformation with imported keys"` `action="transform-create-tokenization-transformation-with-imported-keys"` `businessObject="transform"`
- `displayName="Import key version into tokenization transformation"` `action="transform-import-key-version-into-tokenization-transformation"` `businessObject="transform"`
- `displayName="Retrieve tokenization keys"` `action="transform-list-tokenization-keys"` `businessObject="transform"`
- `displayName="Retrieve tokenization key"` `action="transform-read-tokenization-key"` `businessObject="transform"`
- `displayName="Configure named encryption key"` `action="transform-configure-named-encryption-key"` `businessObject="transform"`
- `displayName="Rotate tokenization key"` `action="transform-rotate-tokenization-key"` `businessObject="transform"`
- `displayName="Trim key versions"` `action="transform-trim-key-versions"` `businessObject="transform"`
- `displayName="Export decoded tokenization tokens"` `action="transform-export-decoded-tokenization-tokens"` `businessObject="transform"`
- `displayName="Restore tokenization state"` `action="transform-restore-tokenization-state"` `businessObject="transform"`
- `displayName="Snapshot tokenization state"` `action="transform-snapshot-tokenization-state"` `businessObject="transform"`
- `displayName="Check if tokenized"` `action="transform-check-tokenized"` `businessObject="transform"`
- `displayName="Delete tokenized data"` `action="transform-delete-tokenized"` `businessObject="transform"`
- `displayName="Look up token"` `action="transform-look-up-token"` `businessObject="transform"`
- `displayName="Delete token"` `action="transform-delete-token"` `businessObject="transform"`
- `displayName="Validate token"` `action="transform-validate-token"` `businessObject="transform"`
- `displayName="Retrieve token metadata"` `action="transform-retrieve-token-metadata"` `businessObject="transform"`
- `displayName="Retrieve alphabets"` `action="transform-list-alphabets"` `businessObject="transform"`
- `displayName="Retrieve alphabet"` `action="transform-read-alphabet"` `businessObject="transform"`
- `displayName="Create or update alphabet"` `action="transform-write-alphabet"` `businessObject="transform"`
- `displayName="Delete alphabet"` `action="transform-delete-alphabet"` `businessObject="transform"`
- `displayName="Retrieve roles"` `action="transform-list-roles"` `businessObject="transform"`
- `displayName="Retrieve role"` `action="transform-read-role"` `businessObject="transform"`
- `displayName="Create or update role"` `action="transform-write-role"` `businessObject="transform"`
- `displayName="Delete role"` `action="transform-delete-role"` `businessObject="transform"`
- `displayName="Retrieve stores"` `action="transform-list-stores"` `businessObject="transform"`
- `displayName="Retrieve store"` `action="transform-read-store"` `businessObject="transform"`
- `displayName="Create or update store"` `action="transform-write-store"` `businessObject="transform"`
- `displayName="Delete store"` `action="transform-delete-store"` `businessObject="transform"`
- `displayName="Apply store schema"` `action="transform-apply-store-schema"` `businessObject="transform"`
- `displayName="Retrieve templates"` `action="transform-list-templates"` `businessObject="transform"`
- `displayName="Retrieve template"` `action="transform-read-template"` `businessObject="transform"`
- `displayName="Create or update template"` `action="transform-write-template"` `businessObject="transform"`
- `displayName="Delete template"` `action="transform-delete-template"` `businessObject="transform"`
- `displayName="Retrieve cache configuration"` `action="transform-read-cache-configuration"` `businessObject="transform"`
- `displayName="Configure cache"` `action="transform-configure-cache"` `businessObject="transform"`
- `displayName="Retrieve wrapping key"` `action="transform-retrieve-wrapping-key"` `businessObject="transform"`

### AWS (`aws`)
- `displayName="Configure AWS root IAM credentials"` `action="aws-configure-root-iam-credentials"` `businessObject="aws"`
- `displayName="Retrieve AWS root IAM credentials configuration"` `action="aws-read-root-iam-credentials-configuration"` `businessObject="aws"`
- `displayName="Rotate AWS root IAM credentials"` `action="aws-rotate-root-iam-credentials"` `businessObject="aws"`
- `displayName="Configure AWS lease settings"` `action="aws-configure-lease"` `businessObject="aws"`
- `displayName="Retrieve AWS lease configuration"` `action="aws-read-lease-configuration"` `businessObject="aws"`
- `displayName="Generate AWS credentials"` `action="aws-generate-credentials"` `businessObject="aws"`
- `displayName="Generate AWS credentials with parameters"` `action="aws-generate-credentials-with-parameters"` `businessObject="aws"`
- `displayName="Generate AWS STS credentials"` `action="aws-generate-sts-credentials"` `businessObject="aws"`
- `displayName="Generate AWS STS credentials with parameters"` `action="aws-generate-sts-credentials-with-parameters"` `businessObject="aws"`
- `displayName="Retrieve AWS roles"` `action="aws-list-roles"` `businessObject="aws"`
- `displayName="Retrieve AWS role"` `action="aws-read-role"` `businessObject="aws"`
- `displayName="Create or update AWS role"` `action="aws-write-role"` `businessObject="aws"`
- `displayName="Delete AWS role"` `action="aws-delete-role"` `businessObject="aws"`
- `displayName="Retrieve AWS static roles"` `action="aws-list-static-roles"` `businessObject="aws"`
- `displayName="Retrieve AWS static role by name"` `action="aws-read-static-roles-name"` `businessObject="aws"`
- `displayName="Create or update AWS static role by name"` `action="aws-write-static-roles-name"` `businessObject="aws"`
- `displayName="Delete AWS static role by name"` `action="aws-delete-static-roles-name"` `businessObject="aws"`
- `displayName="Retrieve AWS static credentials by name"` `action="aws-read-static-creds-name"` `businessObject="aws"`

### Azure (`azure`)
- `displayName="Retrieve Azure configuration"` `action="azure-read-configuration"` `businessObject="azure"`
- `displayName="Configure Azure credentials"` `action="azure-configure"` `businessObject="azure"`
- `displayName="Delete Azure configuration"` `action="azure-delete-configuration"` `businessObject="azure"`
- `displayName="Rotate Azure root credentials"` `action="azure-rotate-root"` `businessObject="azure"`
- `displayName="Generate Azure credentials"` `action="azure-request-service-principal-credentials"` `businessObject="azure"`
- `displayName="Retrieve Azure roles"` `action="azure-list-roles"` `businessObject="azure"`
- `displayName="Retrieve Azure role"` `action="azure-read-role"` `businessObject="azure"`
- `displayName="Create or update Azure role"` `action="azure-write-role"` `businessObject="azure"`
- `displayName="Delete Azure role"` `action="azure-delete-role"` `businessObject="azure"`

### GCP (`gcp`)
- `displayName="Retrieve configuration"` `action="google-cloud-read-configuration"` `businessObject="gcp"`
- `displayName="Configure google cloud"` `action="google-cloud-configure"` `businessObject="gcp"`
- `displayName="Rotate root credentials"` `action="google-cloud-rotate-root-credentials"` `businessObject="gcp"`
- `displayName="Retrieve rolesets"` `action="google-cloud-list-rolesets"` `businessObject="gcp"`
- `displayName="Retrieve roleset"` `action="google-cloud-read-roleset"` `businessObject="gcp"`
- `displayName="Create or update roleset"` `action="google-cloud-write-roleset"` `businessObject="gcp"`
- `displayName="Delete roleset"` `action="google-cloud-delete-roleset"` `businessObject="gcp"`
- `displayName="Rotate roleset"` `action="google-cloud-rotate-roleset"` `businessObject="gcp"`
- `displayName="Rotate roleset key"` `action="google-cloud-rotate-roleset-key"` `businessObject="gcp"`
- `displayName="Generate roleset key (POST)"` `action="google-cloud-generate-roleset-key"` `businessObject="gcp"`
- `displayName="Generate roleset key (GET)"` `action="google-cloud-generate-roleset-key2"` `businessObject="gcp"`
- `displayName="Generate roleset access token (POST)"` `action="google-cloud-generate-roleset-access-token"` `businessObject="gcp"`
- `displayName="Generate roleset access token (GET)"` `action="google-cloud-generate-roleset-access-token2"` `businessObject="gcp"`
- `displayName="Retrieve impersonated accounts"` `action="google-cloud-list-impersonated-accounts"` `businessObject="gcp"`
- `displayName="Retrieve impersonated account"` `action="google-cloud-read-impersonated-account"` `businessObject="gcp"`
- `displayName="Create or update impersonated account"` `action="google-cloud-write-impersonated-account"` `businessObject="gcp"`
- `displayName="Delete impersonated account"` `action="google-cloud-delete-impersonated-account"` `businessObject="gcp"`
- `displayName="Generate impersonated account access token (GET)"` `action="google-cloud-generate-impersonated-account-access-token"` `businessObject="gcp"`
- `displayName="Generate impersonated account access token (POST)"` `action="google-cloud-generate-impersonated-account-access-token2"` `businessObject="gcp"`
- `displayName="Retrieve static accounts"` `action="google-cloud-list-static-accounts"` `businessObject="gcp"`
- `displayName="Retrieve static account"` `action="google-cloud-read-static-account"` `businessObject="gcp"`
- `displayName="Create or update static account"` `action="google-cloud-write-static-account"` `businessObject="gcp"`
- `displayName="Delete static account"` `action="google-cloud-delete-static-account"` `businessObject="gcp"`
- `displayName="Generate static account key (POST)"` `action="google-cloud-generate-static-account-key"` `businessObject="gcp"`
- `displayName="Generate static account key (GET)"` `action="google-cloud-generate-static-account-key2"` `businessObject="gcp"`
- `displayName="Rotate static account key"` `action="google-cloud-rotate-static-account-key"` `businessObject="gcp"`
- `displayName="Generate static account access token (POST)"` `action="google-cloud-generate-static-account-access-token"` `businessObject="gcp"`
- `displayName="Generate static account access token (GET)"` `action="google-cloud-generate-static-account-access-token2"` `businessObject="gcp"`

### GCP KMS (`gcpkms`)
- `displayName="Retrieve GCP KMS configuration"` `action="google-cloud-kms-read-configuration"` `businessObject="gcpkms"`
- `displayName="Configure GCP KMS"` `action="google-cloud-kms-configure"` `businessObject="gcpkms"`
- `displayName="Delete GCP KMS configuration"` `action="google-cloud-kms-delete-configuration"` `businessObject="gcpkms"`
- `displayName="Encrypt a plaintext value using a named key"` `action="google-cloud-kms-encrypt"` `businessObject="gcpkms"`
- `displayName="Decrypt a ciphertext value using a named key"` `action="google-cloud-kms-decrypt"` `businessObject="gcpkms"`
- `displayName="Re-encrypt with GCP KMS"` `action="google-cloud-kms-reencrypt"` `businessObject="gcpkms"`
- `displayName="Sign with GCP KMS"` `action="google-cloud-kms-sign"` `businessObject="gcpkms"`
- `displayName="Verify with GCP KMS"` `action="google-cloud-kms-verify"` `businessObject="gcpkms"`
- `displayName="Retrieve GCP KMS keys"` `action="google-cloud-kms-list-keys"` `businessObject="gcpkms"`
- `displayName="Retrieve GCP KMS key"` `action="google-cloud-kms-read-key"` `businessObject="gcpkms"`
- `displayName="Create or update GCP KMS key"` `action="google-cloud-kms-write-key"` `businessObject="gcpkms"`
- `displayName="Delete GCP KMS key"` `action="google-cloud-kms-delete-key"` `businessObject="gcpkms"`
- `displayName="Retrieve GCP KMS key configuration"` `action="google-cloud-kms-read-key-configuration"` `businessObject="gcpkms"`
- `displayName="Configure GCP KMS key"` `action="google-cloud-kms-configure-key"` `businessObject="gcpkms"`
- `displayName="Rotate GCP KMS key"` `action="google-cloud-kms-rotate-key"` `businessObject="gcpkms"`
- `displayName="Trim GCP KMS key versions (POST)"` `action="google-cloud-kms-trim-key-versions"` `businessObject="gcpkms"`
- `displayName="Trim GCP KMS key versions (DELETE)"` `action="google-cloud-kms-trim-key-versions2"` `businessObject="gcpkms"`
- `displayName="Retrieve GCP KMS public key"` `action="google-cloud-kms-retrieve-public-key"` `businessObject="gcpkms"`
- `displayName="Register GCP KMS key"` `action="google-cloud-kms-register-key"` `businessObject="gcpkms"`
- `displayName="Deregister GCP KMS key (POST)"` `action="google-cloud-kms-deregister-key"` `businessObject="gcpkms"`
- `displayName="Deregister GCP KMS key (DELETE)"` `action="google-cloud-kms-deregister-key2"` `businessObject="gcpkms"`

### AliCloud (`alicloud`)
- `displayName="Retrieve AliCloud configuration"` `action="ali-cloud-read-configuration"` `businessObject="alicloud"`
- `displayName="Configure AliCloud"` `action="ali-cloud-configure"` `businessObject="alicloud"`
- `displayName="Delete AliCloud configuration"` `action="ali-cloud-delete-configuration"` `businessObject="alicloud"`
- `displayName="Generate AliCloud credentials"` `action="ali-cloud-generate-credentials"` `businessObject="alicloud"`
- `displayName="Retrieve AliCloud roles"` `action="ali-cloud-list-roles"` `businessObject="alicloud"`
- `displayName="Retrieve AliCloud role"` `action="ali-cloud-read-role"` `businessObject="alicloud"`
- `displayName="Create or update AliCloud role"` `action="ali-cloud-write-role"` `businessObject="alicloud"`
- `displayName="Delete AliCloud role"` `action="ali-cloud-delete-role"` `businessObject="alicloud"`

### Consul (`consul`)
- `displayName="Retrieve Consul access configuration"` `action="consul-read-access-configuration"` `businessObject="consul"`
- `displayName="Configure Consul access"` `action="consul-configure-access"` `businessObject="consul"`
- `displayName="Generate Consul credentials"` `action="consul-generate-credentials"` `businessObject="consul"`
- `displayName="Retrieve Consul roles"` `action="consul-list-roles"` `businessObject="consul"`
- `displayName="Retrieve Consul role"` `action="consul-read-role"` `businessObject="consul"`
- `displayName="Create or update Consul role"` `action="consul-write-role"` `businessObject="consul"`
- `displayName="Delete Consul role"` `action="consul-delete-role"` `businessObject="consul"`

### Nomad (`nomad`)
- `displayName="Retrieve Nomad access configuration"` `action="nomad-read-access-configuration"` `businessObject="nomad"`
- `displayName="Configure Nomad access"` `action="nomad-configure-access"` `businessObject="nomad"`
- `displayName="Delete Nomad access configuration"` `action="nomad-delete-access-configuration"` `businessObject="nomad"`
- `displayName="Retrieve Nomad lease configuration"` `action="nomad-read-lease-configuration"` `businessObject="nomad"`
- `displayName="Configure Nomad lease"` `action="nomad-configure-lease"` `businessObject="nomad"`
- `displayName="Delete Nomad lease configuration"` `action="nomad-delete-lease-configuration"` `businessObject="nomad"`
- `displayName="Generate Nomad credentials"` `action="nomad-generate-credentials"` `businessObject="nomad"`
- `displayName="Retrieve Nomad roles"` `action="nomad-list-roles"` `businessObject="nomad"`
- `displayName="Retrieve Nomad role"` `action="nomad-read-role"` `businessObject="nomad"`
- `displayName="Create or update Nomad role"` `action="nomad-write-role"` `businessObject="nomad"`
- `displayName="Delete Nomad role"` `action="nomad-delete-role"` `businessObject="nomad"`

### RabbitMQ (`rabbitmq`)
- `displayName="Configure RabbitMQ connection"` `action="rabbit-mq-configure-connection"` `businessObject="rabbitmq"`
- `displayName="Retrieve RabbitMQ lease configuration"` `action="rabbit-mq-read-lease-configuration"` `businessObject="rabbitmq"`
- `displayName="Configure RabbitMQ lease"` `action="rabbit-mq-configure-lease"` `businessObject="rabbitmq"`
- `displayName="Request RabbitMQ credentials"` `action="rabbit-mq-request-credentials"` `businessObject="rabbitmq"`
- `displayName="Retrieve RabbitMQ roles"` `action="rabbit-mq-list-roles"` `businessObject="rabbitmq"`
- `displayName="Retrieve RabbitMQ role"` `action="rabbit-mq-read-role"` `businessObject="rabbitmq"`
- `displayName="Create or update RabbitMQ role"` `action="rabbit-mq-write-role"` `businessObject="rabbitmq"`
- `displayName="Delete RabbitMQ role"` `action="rabbit-mq-delete-role"` `businessObject="rabbitmq"`

### Kubernetes (`kubernetes`)
- `displayName="Check Kubernetes configuration"` `action="kubernetes-check-configuration"` `businessObject="kubernetes"`
- `displayName="Retrieve Kubernetes configuration"` `action="kubernetes-read-configuration"` `businessObject="kubernetes"`
- `displayName="Configure Kubernetes"` `action="kubernetes-configure"` `businessObject="kubernetes"`
- `displayName="Delete Kubernetes configuration"` `action="kubernetes-delete-configuration"` `businessObject="kubernetes"`
- `displayName="Generate Kubernetes credentials"` `action="kubernetes-generate-credentials"` `businessObject="kubernetes"`
- `displayName="Retrieve Kubernetes roles"` `action="kubernetes-list-roles"` `businessObject="kubernetes"`
- `displayName="Retrieve Kubernetes role"` `action="kubernetes-read-role"` `businessObject="kubernetes"`
- `displayName="Create or update Kubernetes role"` `action="kubernetes-write-role"` `businessObject="kubernetes"`
- `displayName="Delete Kubernetes role"` `action="kubernetes-delete-role"` `businessObject="kubernetes"`

### MongoDB Atlas (`mongodbatlas`)
- `displayName="Retrieve MongoDB Atlas configuration"` `action="mongo-db-atlas-read-configuration"` `businessObject="mongodbatlas"`
- `displayName="Configure MongoDB Atlas"` `action="mongo-db-atlas-configure"` `businessObject="mongodbatlas"`
- `displayName="Generate MongoDB Atlas credentials"` `action="mongo-db-atlas-generate-credentials"` `businessObject="mongodbatlas"`
- `displayName="Generate MongoDB Atlas credentials (alternate)"` `action="mongo-db-atlas-generate-credentials2"` `businessObject="mongodbatlas"`
- `displayName="Retrieve MongoDB Atlas roles"` `action="mongo-db-atlas-list-roles"` `businessObject="mongodbatlas"`
- `displayName="Retrieve MongoDB Atlas role"` `action="mongo-db-atlas-read-role"` `businessObject="mongodbatlas"`
- `displayName="Create or update MongoDB Atlas role"` `action="mongo-db-atlas-write-role"` `businessObject="mongodbatlas"`
- `displayName="Delete MongoDB Atlas role"` `action="mongo-db-atlas-delete-role"` `businessObject="mongodbatlas"`

### Terraform Cloud (`terraform`)
- `displayName="Retrieve Terraform Cloud configuration"` `action="terraform-cloud-read-configuration"` `businessObject="terraform"`
- `displayName="Configure Terraform Cloud"` `action="terraform-cloud-configure"` `businessObject="terraform"`
- `displayName="Delete Terraform Cloud configuration"` `action="terraform-cloud-delete-configuration"` `businessObject="terraform"`
- `displayName="Generate Terraform Cloud credentials"` `action="terraform-cloud-generate-credentials"` `businessObject="terraform"`
- `displayName="Generate Terraform Cloud credentials (alternate)"` `action="terraform-cloud-generate-credentials2"` `businessObject="terraform"`
- `displayName="Retrieve Terraform Cloud roles"` `action="terraform-cloud-list-roles"` `businessObject="terraform"`
- `displayName="Retrieve Terraform Cloud role"` `action="terraform-cloud-read-role"` `businessObject="terraform"`
- `displayName="Create or update Terraform Cloud role"` `action="terraform-cloud-write-role"` `businessObject="terraform"`
- `displayName="Delete Terraform Cloud role"` `action="terraform-cloud-delete-role"` `businessObject="terraform"`
- `displayName="Rotate Terraform Cloud role"` `action="terraform-cloud-rotate-role"` `businessObject="terraform"`

### System — Leases (`leases`)
- `displayName="List leases"` `action="leases-list"` `businessObject="leases"`
- `displayName="Count leases"` `action="leases-count"` `businessObject="leases"`
- `displayName="Read lease metadata"` `action="leases-read-lease"` `businessObject="leases"`
- `displayName="List leases by prefix"` `action="leases-look-up"` `businessObject="leases"`
- `displayName="Renew lease"` `action="leases-renew-lease"` `businessObject="leases"`
- `displayName="Renew lease by ID"` `action="leases-renew-lease-with-id"` `businessObject="leases"`
- `displayName="Revoke lease"` `action="leases-revoke-lease"` `businessObject="leases"`
- `displayName="Revoke lease by ID"` `action="leases-revoke-lease-with-id"` `businessObject="leases"`
- `displayName="Revoke leases by prefix"` `action="leases-revoke-lease-with-prefix"` `businessObject="leases"`
- `displayName="Force revoke leases by prefix"` `action="leases-force-revoke-lease-with-prefix"` `businessObject="leases"`
- `displayName="Tidy leases"` `action="leases-tidy"` `businessObject="leases"`

### PKI (`pki`)
The PKI engine contains over 200 operations covering certificate issuance, issuers, keys, roles, CRL management, ACME, EST, SCEP, OCSP, and KMIP integration. The operation keys all follow the prefix `pki-` and correspond directly to the entries in [`appconnect-connector-hashicorpvault/lib/src/utils/engines/pki/operations.json`](appconnect-connector-hashicorpvault/lib/src/utils/engines/pki/operations.json). Use the `summary` field of each entry as the `displayName` and the operation key as the `action`, with `businessObject="pki"`.

## Policy requirements
- Create policies in an ACE Policy project, not in an Application project.
- A suitable default policy reference is similar to `{DiscoveryConnectorPolicyProject}:Hashicorpvault1`.
- This connector uses `applicationType="online"` and `authenticationMethod="BASIC"`. The policy includes an `<apiUrl>` field for the Vault server URL, a `<nameSpace>` field (default `root`), a `<mountPath>` field (default `userpass`), and an `<enginePath>` field.

## Example policy
```xml
<?xml version="1.0" encoding="UTF-8"?>
<policies>
    <policy longDescription="" policyName="Hashicorpvault1" policyTemplate="online_v1_basic" policyType="hashicorpvault" shortDescription="" version="">
        <credentialName/>
        <applicationVersion>v1</applicationVersion>
        <applicationType>online</applicationType>
        <authenticationMethod>BASIC</authenticationMethod>
        <apiUrl/>
        <nameSpace>root</nameSpace>
        <mountPath>userpass</mountPath>
        <enginePath/>
        <proxyId/>
    </policy>
</policies>
```

## Validation requirements
- Validate policy XML using the applicable ACE Policy schema.
- Refer to [`skills/shared/ace-versions.md`](../ace-versions.md) for schema locations.

## Related files
- [`skills/shared/connector-index.md`](../connector-index.md)
- [`skills/shared/node-types.md`](../node-types.md)
