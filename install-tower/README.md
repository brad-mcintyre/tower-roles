# Ansible role: tower/tower_install  


Installs AND configures the target  version of Ansible and Ansible Tower.

Once installation has been successfully completed, Ansible Tower can be accessed from {{ tower_ip_address }}:80 in your web browser and the admin details will be requested. The username is admin and password is {{ tower_admin_user_password }}

Currently this role has been used to install  Ansible 2.2 and tower 3.0.3  using online install  and  Ansible 2.3 and tower 3.1.3 using bundled
both tested with separate postgres  install as localhost.    


## Warnings
- Role is not fully idempotent  
- Non redhat Rel7 support disabled for now   
- Test playbook is incomplete but mostly covered by Redhat's own checks       

## Requirements

(IF external postgreSQL is used as localhost ,see dependency section below.)


## Variables
|Variable|Required|Default|Choices|Description|
|--------|--------|-------|-------|-----------|
|tower_bundle_install|yes|no |yes/no| Activate towers bundle install mode option - note not tested outside of default 'no' for v 3.0.3 and ignored entirely in version 3.1.3  |
|tower_python_dependencies_303|yes|[list]|| Required python dependency packages for  v3.0.3  online install  |
|tower_non_python_dependencies_303|yes|[list]|| Required non pyhthon packages for v3.0.3  online install  |
|tower_ansible_package_version|yes|ansible-2.2.0.0|ansible-2.2.0.0/ansible-2.3.0.0| Force the installation of particular Ansible version|  
|tower_install_use_artifact_source:|no|blank|true/false/yes/no|whether to use artifactory install, if not itll try an offline install |
|tower_version|yes|3.0.3|3.0.3/3.1.3/3.1.4| The version of tower to be installed. |
|tower_user|yes|rhel|| This is the tower directory owner - needs to exist before role is run  |
|tower_admin_user_password|yes|pass||This is the initial password for the admin Tower user |
|tower_setup_email|yes|no|yes/no|Set up tower email  - not tested .|
|tower_default_from_email|no|''||tower's 'from email address' ignored if tower_setup_email=no |
|tower_email_subject_prefix|no|'[AWX]'||default email subject prefix  - ignored if tower_setup_email=no|
|tower_email_host|no|''|| email host  -  ignored if tower_setup_email=no|
|tower_email_port|no|''||email port  -  ignored if tower_setup_email=no|
|tower_email_host_user|no|''||email user  -  ignored if tower_setup_email=no|
|tower_email_host_password|no|''||email password  -  ignored if tower_setup_email=no|
|tower_email_use_tls|no|True|true/false| Whether to use a TLS (secure) connection when talking to the SMTP server -  ignored if tower_setup_email=no|
|tower_awx_proot_enabled|yes|False|True/false| All playbooks are executed via the awx filesystem user. For running jobs, Ansible Tower defaults to offering job isolation via Linux namespacing and chroots. This projection ensures jobs can only access playbooks and roles from the Project directory for that job template and common locations such as /opt. Playbooks are not able to access roles, playbooks, or data from other Projects by default., unless  tower_awx_proot_enabled= false  |
|tower_socket_io_listner_port|yes|8080| port number| WebSockets port for live events **ignored for  3.1.3**    |
|tower_remote_host_headers|yes|"['REMOTE_ADDR', 'REMOTE_HOST']"||change these if needed as per tower administration manuals to support proxies ,**ignored for  3.1.3**  |
|tower_postgresql_database_name|yes|tower|| The name of the tower postgres database  |
|tower_postgresql_database_host|no|localhost|| The host name of external database for tower|
|tower_postgresql_database_user|no|ansible||The database user account  |
|tower_postgresql_database_user_password|no|pass||The database user password |
|tower_postgresql_database_port|yes|5432|any port| The database connection port|
|tower_database_external|yes|yes|Yes/no|If yes, use externally defined database if no, let tower install installs database software |  
|tower_redis_password|yes|password||Sets the password for the redis fact cache **ignored for  3.1.3**|
|tower_redis_ip|yes|localhost||Sets the url  of the redis fact cashe  **ignored for  3.1.3**|
|tower_munin_password|yes|'tower'|| password needed for  munin ( built in monitor for tower ) **ignored for  3.1.3**|
|tower_files_unpacked_dir|yes|ansible-tower-setup-bundle-{{tower_version}}-1.el7 || Name of the directory location  of the tower install as unpacked directory off {{tower_unpack_location}  **3.1.3/3.1.4 only** |
|tower_files_in_303|yes|ansible-tower-setup-latest.tar.gz||Name of the directory location  of the tower install as unpacked directory off {{tower_unpack_location}  **3.0.3 only**
|tower_files_in|yes|{{tower_files_in_313}}||Name of tar file input into role **3.1.3 only**|  
|tower_tar_location|yes|/tmp|| local directory to move the tar file to before unpacking |
|tower_unpack_location|yes|/usr/local/|| local directory location where tower will be unpacked to |
|tower_install_is_clustered|yes| false || Set true if this install is a clustered installation **3.1.3 only** |
|tower_clustered_hosts| yes  |[] || The list of clustered host names to be set for a clustered install  **3.1.3 only**,  not tested |
|tower_rabbitmq_username|yes| tower|| new for  **3.1.3/3.1.4 only **, usercode and password required for the rabbitmq |  
|tower_rabbitmq_password|yes| tower|| new for  **3.1.3/3.1.4 only **, usercode and password required for the rabbitmq |  


## Dependencies

This role depends on the following roles under the following conditions  :

if  ```tower_database_external=yes ``` Then  postgres needs to be installed
      on the ```tower_postgresql_database_host```

roles  that are of use are :
```

       - postgresql/install
       - postgresql/createDB
       - postgresql/configure_prof
       - postgresql/configure_hba
       - postgresql/configure_online_backup
       - tower/tower_install

```


however if used the following variable relationships are needed:

 ```
postgresql_createdb_databases:
                  - name:  {{tower_postgresql_database_name}}
                    username: {{tower_postgresql_database_user}}
                    userpassword: {{tower_postgresql_database_user_password}}
                    encoding: 'UTF-8'    
```

## Examples

```YAML
- hosts: tower-servers
  vars:
      postgresql_createdb_databases:
                        - name:  tower
                          username: ansible
                          userpassword: pass
                          encoding: 'UTF-8'

      postgresql_common_version: 9.4
      postgresql_common_version_contracted: 94
      postgresql_common_set: 'NOT92'

      tower_postgresql_database_host: localhost

      # for  3.1.3  omit for 3.0.3   
      tower_ansible_package_version: ansible-2.3.0.0
      tower_version: 3.1.3


       artifactory_url: "http://172.17.203.21"

  roles:
    - { role: postgresql/common}
    - { role: postgresql/install}
    - { role: postgresql/createDB}
    - { role: postgresql/configure_prof}
    - { role: postgresql/configure_hba}
    - { role: postgresql/configure_online_backup}
    - { role: tower/tower/install}




```
