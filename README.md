# ans_rols

В проекте четыре инстанса:

tomcat, jenkins, gitlab, artifactory

ОС установленная на инстансы – RedHat  или  Ubuntu

каждому из них отведена своя роль и предназначение

сгруппированы :

[stage_servers]
jenkins   ansible_host=192.168.33.14
gitlab    ansible_host=192.168.33.12

[prod_servers]
tomcat   ansible_host=192.168.33.13

[dev_servers]
artifactory    ansible_host=192.168.33.11

Vagrant поднимает инстанс командой vagrant up [instance_name]

точно так же стопает   vagrant halt [instance_name]

после изменений в конфигурационных файлах – Vagrantfile     ansible     playbook.yml
для выполнения  изменений  необходимо выполнить команду 
vagrant reload [instance_name] --provision

в конфигурации инстансов (содержится в Vagrantfile)  выставляются требования к каждому инстансу – RAM , HDD, core number 

Эти значения могут быть различны для каждого инстанса и задаются в VagrantfileS.

Провизионинг инстансов производится с помощью Ansible   а именно прописан в файлах playbook.yml

Используя roles (Ansible) группируем задачи провизионинга, а именно:

описываем в playbook.yml для каких инстансов какие роли применять

роли:

base  - ставим необходимые программы и подключаем дополнительные репозитории
(во всех ролях есть механизм, какие программы и как ставить на инстанс в зависимости от используемой ОС)

info – выдает заданную информацию про инстансы 

java – устанавливает java 1.8.x  JDK

selinux -  в этой роли playbook запускает скрипт, отключающий selinux

web-service – устанавливаем web_server ( используя blocks для разных ОС ), копируем на него свою web-страничку и делаем так, чтоб он всегда стартовал при перезагрузке.


