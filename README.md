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

wso2ei_enable_custom_configuration:     no

wso2ei_verifyHostname:                  false

wso2ei_userAgent:                       'WSO2 EI 6.1.1'
wso2ei_server:                          'WSO2 EI 6.1.1'
wso2ei_SynapseConfig_ServerName:        'WSO2 Carbon Server'

wso2ei_enable_VFS_transport: no
wso2ei_enable_secure_VFS_transport: no


wso2ei_source_cert_dirpath:             "/etc/letsencrypt/live/wso2ei.example.com"
wso2ei_source_cert_file:                "{{ wso2ei_source_cert_dirpath }}/fullchain.pem"
wso2ei_source_cert_private_file:        "{{ wso2ei_source_cert_dirpath }}/privkey.pem"
wso2ei_source_pkcs12_file_basename:     'klogwso2ei.pfx'
wso2ei_source_pkcs12_file_name:         "{{ wso2ei_source_cert_dirpath }}/{{ wso2ei_source_pkcs12_file_basename }}"
wso2ei_source_pkcs12_alias_name:        'klogwso2ei'
wso2ei_source_pkcs12_password:          'mySecurePassword'

wso2ei_jks_dirpath:                     "{{ wso2ei_install_appdir_fullpath }}/repository/resources/security"

wso2ei_jks_web_keystore_file_basename:  'wso2carbon.jks'
wso2ei_jks_web_keystore_file_name:      "{{ wso2ei_jks_dirpath }}/{{ wso2ei_jks_web_keystore_file_basename }}"
wso2ei_jks_web_keystore_password:       'wso2carbon'

wso2ei_cert_exported_jks_file_name:         "{{ wso2ei_jks_dirpath }}/klogwso2eifullchainpriv.pem"
wso2ei_jks_client_truststore_file_basename: 'client-truststore.jks'
wso2ei_jks_client_truststore_file_name:     "{{ wso2ei_jks_dirpath }}/{{ wso2ei_jks_client_truststore_file_basename }}"
wso2ei_jks_client_truststore_password:      'wso2carbon'

wso2ei_jks_primary_keystore_file_basename:              'klogwso2ei_internal.jks'
wso2ei_jks_primary_keystore_file_name:                  "{{ wso2ei_jks_dirpath }}/{{ wso2ei_jks_primary_keystore_file_basename }}"
wso2ei_jks_primary_keystore_password:                   'mySecurePasswordInternal'
wso2ei_jks_primary_keystore_cn:                         'wso2ei.example.com'
wso2ei_jks_primary_keystore_o:                          'Example Company'
wso2ei_jks_primary_keystore_ou:                         'IT Department'
wso2ei_jks_primary_keystore_l:                          'Surabaya'
wso2ei_jks_primary_keystore_s:                          'East Java'
wso2ei_jks_primary_keystore_c:                          'ID'
wso2ei_jks_primary_keystore_validity_days:              360
wso2ei_jks_primary_keystore_keyalg:                     'RSA'
wso2ei_jks_primary_keystore_keysize:                    2048
wso2ei_jks_primary_keystore_SubjectAlternativeName_dns: 'wso2ei.example.com'
wso2ei_jks_primary_keystore_AuthorityInfoAccess_email:  "{{ wso2ei_install_git_user_email }}"

wso2ei_JVM_MEM_OPTS:                    "-Xms256m -Xmx1024m"
wso2ei_analytics_JVM_MEM_OPTS:          "-Xms256m -Xmx2048m"
wso2ei_broker_JVM_MEM_OPTS:             "-Xms1024m -Xmx2048m"
wso2ei_business_process_JVM_MEM_OPTS:   "-Xms256m -Xmx1024m"
wso2ei_msf4j_JVM_MEM_OPTS:              "-Xms256m -Xmx1024m"

wso2ei_validator_CPU:             800
wso2ei_validator_RAM:             2047
wso2ei_validator_swap:            2047
wso2ei_validator_freeDisk:        1024
wso2ei_validator_ulimit:          4096
wso2ei_validator_certFingerprint: '02:FB:AA:5F:20:64:49:4A:27:29:55:71:83:F7:46:CD'
wso2ei_validator_initHeapSize:    256
wso2ei_validator_maxHeapSize:     512
wso2ei_validator_maxPermGenSize:  256

wso2ei_analytics_validator_CPU:             "{{ wso2ei_validator_CPU }}"
wso2ei_analytics_validator_RAM:             "{{ wso2ei_validator_RAM }}"
wso2ei_analytics_validator_swap:            "{{ wso2ei_validator_swap }}"
wso2ei_analytics_validator_freeDisk:        "{{ wso2ei_validator_freeDisk }}"
wso2ei_analytics_validator_ulimit:          "{{ wso2ei_validator_ulimit }}"
wso2ei_analytics_validator_certFingerprint: "{{ wso2ei_validator_certFingerprint }}"
wso2ei_analytics_validator_initHeapSize:    "{{ wso2ei_validator_initHeapSize }}"
wso2ei_analytics_validator_maxHeapSize:     "{{ wso2ei_validator_maxHeapSize }}"
wso2ei_analytics_validator_maxPermGenSize:  "{{ wso2ei_validator_maxPermGenSize }}"

wso2ei_broker_validator_CPU:              "{{ wso2ei_validator_CPU }}"
wso2ei_broker_validator_RAM:              "{{ wso2ei_validator_RAM }}"
wso2ei_broker_validator_swap:             "{{ wso2ei_validator_swap }}"
wso2ei_broker_validator_freeDisk:         "{{ wso2ei_validator_freeDisk }}"
wso2ei_broker_validator_ulimit:           "{{ wso2ei_validator_ulimit }}"
wso2ei_broker_validator_certFingerprint:  "{{ wso2ei_validator_certFingerprint }}"
wso2ei_broker_validator_initHeapSize:     "{{ wso2ei_validator_initHeapSize }}"
wso2ei_broker_validator_maxHeapSize:      "{{ wso2ei_validator_maxHeapSize }}"
wso2ei_broker_validator_maxPermGenSize:   "{{ wso2ei_validator_maxPermGenSize }}"

wso2ei_business_process_validator_CPU:              "{{ wso2ei_validator_CPU }}"
wso2ei_business_process_validator_RAM:              "{{ wso2ei_validator_RAM }}"
wso2ei_business_process_validator_swap:             "{{ wso2ei_validator_swap }}"
wso2ei_business_process_validator_freeDisk:         "{{ wso2ei_validator_freeDisk }}"
wso2ei_business_process_validator_ulimit:           "{{ wso2ei_validator_ulimit }}"
wso2ei_business_process_validator_certFingerprint:  "{{ wso2ei_validator_certFingerprint }}"
wso2ei_business_process_validator_initHeapSize:     "{{ wso2ei_validator_initHeapSize }}"
wso2ei_business_process_validator_maxHeapSize:      "{{ wso2ei_validator_maxHeapSize }}"
wso2ei_business_process_validator_maxPermGenSize:   "{{ wso2ei_validator_maxPermGenSize }}"
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
      wso2ei_JVM_MEM_OPTS:                    "-Xms256m -Xmx2048m"
      wso2ei_analytics_JVM_MEM_OPTS:          "-Xms256m -Xmx2048m"
      wso2ei_broker_JVM_MEM_OPTS:             "-Xms1024m -Xmx2048m"
      wso2ei_business_process_JVM_MEM_OPTS:   "-Xms256m -Xmx2048m"
      wso2ei_msf4j_JVM_MEM_OPTS:              "-Xms256m -Xmx1024m"
      wso2ei_validator_CPU:                   800
      wso2ei_validator_RAM:                   2047
      wso2ei_validator_swap:                  2047
      wso2ei_validator_freeDisk:              1024
      wso2ei_validator_ulimit:                4096
      wso2ei_validator_certFingerprint:       '02:FB:AA:5F:20:64:49:4A:27:29:55:71:83:F7:46:CD'
      wso2ei_validator_initHeapSize:          256
      wso2ei_validator_maxHeapSize:           512
      wso2ei_validator_maxPermGenSize:        256
```

License
-------

BSD

Author Information
------------------

This role was created in 2017 by [Adi Priyanto](https://github.com/adipriyantobpn) as a learning purpose for community.