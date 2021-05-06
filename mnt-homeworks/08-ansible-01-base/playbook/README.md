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
9.	ssh
10.	Сделал
11.	Проверил, все правильно 
12.	Заполнил 

