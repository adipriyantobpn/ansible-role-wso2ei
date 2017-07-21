Ansible Role: WSO2 Enterprise Integrator
=========

An Ansible Role to install WSO2 Enterprise Integrator

Before using this role, WSO2 Enterprise Integrator installer files must be placed on the playbook files directory.
Make sure that those files have same version specified on the role variables.

Requirements
------------

This role needs no special requirements, except WSO2 Enterprise Integrator installers and sudo access

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):


```yaml
---
wso2ei_version:                         "6.1.1"
wso2ei_installer_filename:              "wso2ei-{{ wso2ei_version }}.zip"
wso2ei_use_local_installer:             no
wso2ei_local_installer_path:            "{{ x_ansible_download_dir | default(ansible_env.HOME + '/.ansible/tmp/downloads') }}"
wso2ei_tmp_dir:                         "/tmp"
wso2ei_install_basedir:                 "/opt"
wso2ei_install_appdirname:              "wso2ei-{{ wso2ei_version }}"
wso2ei_install_appdir_fullpath:         "{{ wso2ei_install_basedir }}/{{ wso2ei_install_appdirname }}"

wso2ei_install_source_control_tracked:  yes
wso2ei_install_git_user_name:           'John Doe'
wso2ei_install_git_user_email:          'john.doe@example.com'
```

Dependencies
------------

None

Example Playbook
----------------

```yaml
---
- name: Prepare CentOS 7 server
  hosts: centos7
  roles:
    - role: adipriyantobpn.wso2ei
      wso2ei_version:                         "6.1.1"
      wso2ei_use_local_installer:             yes
      wso2ei_local_installer_path:            "/vagrant/provisions/ansible/files"
      wso2ei_tmp_dir:                         "/tmp"
      wso2ei_install_basedir:                 "/opt"
      wso2ei_install_source_control_tracked:  yes
      wso2ei_install_git_user_name:           'Adi Priyanto'
      wso2ei_install_git_user_email:          'adipriyanto.bpn@gmail.com'
```

License
-------

BSD

Author Information
------------------

This role was created in 2017 by [Adi Priyanto](https://github.com/adipriyantobpn) as a learning purpose for community.