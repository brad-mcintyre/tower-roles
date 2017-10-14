# Ansible role: Tower-Create-Team

## Overview

This role creates a new Team in Ansible Tower.

## Requirements



## Variables

|Variable|Required|Default|Choices|Description|
|--------|--------|-------|-------|-----------|
|tower_team_name|yes||| Name of the Team to create. |
|tower_team_description|yes|||Description of the Team to create. |
|tower_team_organisation|yes|||Organisation to create the Team in.|
|tower_host_name|yes|||Ansible Tower server name. |
|tower_username| yes||| Ansible Tower username with permissions to create the new Team. |
|tower_password| yes|||Ansible Tower username password.|


## Dependencies


## Examples

```

    - name: Create Tower Team
      hosts: localhost
      gather_facts: False

      roles:
      - role: tower-create-team

```
