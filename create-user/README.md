# Tower role: create-credential

## Overview

This role creates a Tower Credential.

## Requirements (on host that executes module)


- python >= 2.6
- ansible-tower-cli >= 3.0.2

## Variables

|Variable|Required|Default|Choices|Example|Description|
|--------|--------|-------|-------|-----------|---|
|tower_credential_authorize|no||||Should use authroize for net type.|
|tower_credential_autorize_password|no||||Password for net credentials that require authroize.|
|tower_credential_become_method|no|None|<ul><li>None</li><li>sudo</li><li>su</li><li>pbrun</li><li>pfexec</li><li>pmrun</li>||Become method to Use for privledge escalation.|
|tower_credential_become_password|no||||Become password. Use ASK for prompting.|
|tower_credential_client|no||||Client or application ID for azure_rm type.|
|tower_credential_description|no||||The description to use for the credential.|
|tower_credential_domain|||||Domain for openstack type.|
|tower_credential_host|no||||Host for this credential.|
|tower_credential_kind|yes||<ul><li>None</li><li>ssh</li><li>net</li><li>scm</li><li>aws</li><li>rax</li><li>vmware</li><li>satellite6</li><li>cloudforms</li><li>gce</li><li>azure</li><li>azure_rm</li><li>openstack</li>||Type of credential being added.|
|tower_credential_name|yes||||The name to use for the credential.|
|tower_credential_organization|no||||Organization that should own the credential.|
|tower_credential_password|no||||Password for this credential. Use ASK for prompting. secret_key for AWS. api_key for RAX.|
|tower_credential_project|no||||Project that should for this credential.|
|tower_credential_secret|no||||Secret token for azure_rm type.|
|tower_credential_ssh_key_data|no||||SPath to SSH private key.|
|tower_credential_ssh_key_unlock|no||||Secret token for azure_rm type.|
|tower_credential_state|no||present||Unlock password for ssh_key. Use ASK for prompting.|
|tower_credential_secret|no||<ul><li>present</li><li>absent</li>||Desired state of the resource.|
|tower_credential_subscription|no||||Secret token for azure_rm type.|
|tower_credential_team|no||||Team that should own this credential.|
|tower_credential_tenant|no||||Tenant ID for azure_rm type.|
|tower_credential_tower_config_file|no||||Path to the Tower config file.|
|tower_credential_tower_host|no||||URL to your Tower instance.|
|tower_credential_tower_password|no||||Password for your Tower instance.|
|tower_credential_tower_username|no||||Username for your Tower instance.|
|tower_credential_tower_verify_ssl|no|True|||Dis/allow insecure connections to Tower. If no, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.|
|tower_credential_user|no||||User that should own this credential.|
|tower_credential_username|no||||Username for this credential. access_key for AWS.|
|tower_credential_vault_password|no||||Valut password. Use ASK for prompting.|





## Dependencies

No dependencies.

## Examples
