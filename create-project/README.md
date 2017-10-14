# Tower role: create-project

## Overview

This role creates a Tower Project.

## Requirements (on host that executes module)


- python >= 2.6
- ansible-tower-cli >= 3.0.2

## Variables

|Variable|Required|Default|Choices|Example|Description|
|--------|--------|-------|-------|-----------|---|
|tower_project_description|no||||Description to use for the project.|
|tower_project_local_path|no||||The server playbook directory for manual projects.|
|tower_project_name|yes||||Name to use for the project.|
|tower_project_organization|no||||Primary key of organization for project.|
|tower_project_scm_branch|no||||The branch to use for the scm resource.|
|tower_project_scm_clean|no|false|<ul><li>true</li><li>false</li>||Remove local modifications before updating.|
|tower_project_scm_credential|no|||| Name of the credential to use with this scm resource. |
|tower_project_delete_on_update|no|false|<ul><li>true</li><li>false</li>||Remove the repository completely before updating.|
|tower_project_scm_type|no|manual|<ul><li>manual</li><li>git</li><li>hg</li><li>svn</li>||Type of scm resource.|
|tower_project_scm_update_on_launch|no|false|<ul><li>true</li><li>false</li>||Before an update to the local repository before launching a job with this project.|
|tower_project_scm_url|no||||URL of scm resource.|
|tower_project_state|no|present|<ul><li>present</li><li>absent</li>||Path to the Tower config file.|
|tower_project_tower_config_file|no||||Project that should for this credential.|
|tower_host_name|no||||URL to your Tower instance.|
|tower_toweradmin_user_password|no||||Password for your Tower instance.|
|tower_toweradmin_user_name|no||||Username for your Tower instance.|
|tower_project_tower_verify_ssl|no|true|<ul><li>true</li><li>false</li>||Dis/allow insecure connections to Tower. If no, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates|


## Dependencies

No dependencies.

## Examples
