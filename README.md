# bm_tools

## 사용 방법

- inventory 수정
```
$ cat inventory

[vdbench]
vdbench01 ansible_host=192.168.0.18 ansible_user=pure
vdbench02 ansible_host=192.168.0.20 ansible_user=pure
vdbench03 ansible_host=192.168.0.24 ansible_user=pure
vdbench04 ansible_host=192.168.0.19 ansible_user=pure
```
- 실행
```
$ ansible-playbook -i inventory vdbench_install_on_ubuntu.yaml -kK

SSH password:                                                        // Password 입력
BECOME password[defaults to SSH password]:                           // Sudo Password 입력

PLAY [vdbench Install] ***************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ***************************************************************************************************************************************************************************************************
ok: [vdbench03]
ok: [vdbench04]
ok: [vdbench02]
ok: [vdbench01]

TASK [remove firewall] ***************************************************************************************************************************************************************************************************
ok: [vdbench02]
ok: [vdbench03]
ok: [vdbench04]
ok: [vdbench01]

TASK [Install package] ***************************************************************************************************************************************************************************************************
[DEPRECATION WARNING]: Invoking "apt" only once while using a loop via squash_actions is deprecated. Instead of using a loop to supply multiple items and specifying `name: "{{ item }}"`, please use `name: ['default-
jre', 'curl', 'unzip']` and remove the loop. This feature will be removed in version 2.11. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
[DEPRECATION WARNING]: Invoking "apt" only once while using a loop via squash_actions is deprecated. Instead of using a loop to supply multiple items and specifying `name: "{{ item }}"`, please use `name: ['default-
jre', 'curl', 'unzip']` and remove the loop. This feature will be removed in version 2.11. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
[DEPRECATION WARNING]: Invoking "apt" only once while using a loop via squash_actions is deprecated. Instead of using a loop to supply multiple items and specifying `name: "{{ item }}"`, please use `name: ['default-
jre', 'curl', 'unzip']` and remove the loop. This feature will be removed in version 2.11. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
[DEPRECATION WARNING]: Invoking "apt" only once while using a loop via squash_actions is deprecated. Instead of using a loop to supply multiple items and specifying `name: "{{ item }}"`, please use `name: ['default-
jre', 'curl', 'unzip']` and remove the loop. This feature will be removed in version 2.11. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
changed: [vdbench02] => (item=['default-jre', 'curl', 'unzip'])
changed: [vdbench04] => (item=['default-jre', 'curl', 'unzip'])
changed: [vdbench03] => (item=['default-jre', 'curl', 'unzip'])
changed: [vdbench01] => (item=['default-jre', 'curl', 'unzip'])

TASK [Create Download Folder] ********************************************************************************************************************************************************************************************
changed: [vdbench02]
changed: [vdbench04]
changed: [vdbench03]
changed: [vdbench01]

TASK [Package Download] **************************************************************************************************************************************************************************************************
changed: [vdbench02]
changed: [vdbench04]
changed: [vdbench01]
changed: [vdbench03]

TASK [Create vdbench Folder] *********************************************************************************************************************************************************************************************
changed: [vdbench02]
changed: [vdbench01]
changed: [vdbench04]
changed: [vdbench03]

TASK [UnZip vdbench Package] *********************************************************************************************************************************************************************************************
changed: [vdbench02]
changed: [vdbench04]
changed: [vdbench03]
changed: [vdbench01]

PLAY RECAP ***************************************************************************************************************************************************************************************************************
vdbench01                  : ok=7    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
vdbench02                  : ok=7    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
vdbench03                  : ok=7    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
vdbench04                  : ok=7    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
