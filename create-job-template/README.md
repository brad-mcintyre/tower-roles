# Tower role: create-job-template

## Overview

This role creates a Tower Job Template.

## Requirements (on host that executes module)


- python >= 2.6
- ansible-tower-cli >= 3.0.2

## Variables

|Variable|Required|Default|Choices|Example|Description|
|--------|--------|-------|-------|-----------|---|
|tower_job_template_name|yes||||Name to use for the job_template.|
|tower_job_template_ask_credential|no||||Prompt user for credential on launch.|
|tower_job_template_ask_extra_vars|yes||||Prompt user for extra_vars on launch.|
|tower_job_template_ask_inventory|no||||Prompt user for inventory on launch.|
|tower_job_template_ask_job_type|no||||Prompt user for job type on launch.|
|tower_job_template_ask_tags|no||||Prompt user for job tags on launch.|
|tower_job_template_become_enabled|no|||| Should become_enabled. |
|tower_job_template_cloud_credential|no|||| Cloud_credential to use for the job_template. |
|tower_job_template_description|no||||Description to use for the job_template.|
|tower_job_template_extra_vars_path|no||||Path to the extra_vars yaml file.|
|tower_job_template_forks|no||||The number of parallel or simultaneous processes to use while executing the playbook.|
|tower_job_template_host_config_key|no||||Allow provisioning callbacks using this host config key.|
|tower_job_template_inventory|no|||| Inventory to use for the job_template. |
|tower_job_template_job_tags|no||||The job_tags to use for the job_template.|
|tower_job_template_job_type|no||<ul><li>run</li><li>check</li><li>scan</li>||The job_type to use for the job_template.|
|tower_job_template_limit|no||||A host pattern to further constrain the list of hosts managed or affected by the playbook|
|tower_job_template_machine_credential|no||||Machine_credential to use for the job_template.|
|tower_job_template_network_credential|no||||The network_credential to use for the job_template.|
|tower_job_template_playbook|yes||||Playbook to use for the job_template.|
|tower_job_template_project|yes||||Project to use for the job_template.|
|tower_job_template_skip_tags|no||||The skip_tags to use for the job_template.|
|tower_job_template_state|yes|present|<ul><li>present</li><li>absent</li>||Desired state of the resource.|
|tower_job_template_tower_config_file|no||||Path to the Tower config file.|
|tower_host_name|no||||URL to your Tower instance.|
|tower_toweradmin_user_name|no||||Username for your Tower instance.|
|tower_toweradmin_user_password|no||||Password for your Tower instance.
|tower_job_template_tower_verify_ssl|no||||Dis/allow insecure connections to Tower. If no, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.|
|tower_job_template_verbosity|no||<ul><li>verbose</li><li>debug</li>||Control the output level Ansible produces as the playbook runs.|



## Dependencies

No dependencies.

## Examples
