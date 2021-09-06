Домашнее задание 

0.	Подготовительную часть выполнил
1.	ansible-playbook site.yml -i inventory/test.yml
Значение файла some_fact указано в файле group_vars/all/examp.yml 
some_fact: 12
2.	group_vars/all/examp.yml изменил на  изменил на some_fact: all default fact
3.	Запустил на docker  необходимое окружение
4.	Задание
 TASK [Print fact] **************************************************************
ok: [centos7] => {
    "msg": "el"
}
ok: [ubuntu] => {
    "msg": "deb"
}

5.	Изменил 
6.	Вывод:
TASK [Print fact] **************************************************************
ok: [centos7] => {
    "msg": "el default fact"
}
ok: [ubuntu] => {
    "msg": "deb default fact"
}

7.	Ansible-vault encrypt  - зашифровал 
8.	ansible-playbook -i inventory/prod.yml site.yml --ask-vault-pass – все получилось 
9.	control node - Если я правильно это хост с которого ansible выполняет play и в данной задаче нужно определить плагин подходящий для работы ansible-playbook? 
Я считаю подходящий плагин paramiko_ssh  Run tasks via python ssh (paramiko). Для подлючения к винде думаю подойдет psrp Run tasks over Microsoft PowerShell Remoting Protocol.
 
10.	Добавил 
el:
    hosts:
      centos7:
        ansible_connection: docker
  deb:
    hosts:
      ubuntu:
        ansible_connection: docker
  local:
    hosts:
      localhost:
        ansible_connection: local

11.	ansible-playbook -i inventory/prod.yml site.yml --ask-vault-pass
Vault password:

PLAY [Print os facts] *****************************************************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************************************
ok: [localhost]
[DEPRECATION WARNING]: Distribution Ubuntu 18.04 on host ubuntu should use /usr/bin/python3, but is using /usr/bin/python for backward compatibility with prior Ansible releases. A future Ansible release
will default to using the discovered platform python for this host. See https://docs.ansible.com/ansible/2.10/reference_appendices/interpreter_discovery.html for more information. This feature will be
removed in version 2.12. Deprecation warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
ok: [ubuntu]
ok: [centos7]

TASK [Print OS] ***********************************************************************************************************************************************************************************************
ok: [localhost] => {
    "msg": "Ubuntu"
}
ok: [centos7] => {
    "msg": "CentOS"
}
ok: [ubuntu] => {
    "msg": "Ubuntu"
}

TASK [Print fact] *********************************************************************************************************************************************************************************************
ok: [localhost] => {
    "msg": "all default fact"
}
ok: [centos7] => {
    "msg": "el default fact"
}
ok: [ubuntu] => {
    "msg": "deb default fact"
}

PLAY RECAP ****************************************************************************************************************************************************************************************************
centos7                    : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
localhost                  : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
ubuntu                     : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
 
12.	Заполнил можно посмотреть в моем репозитории по следующей ссылке: https://github.com/Andrey-netology/ansible2.git

