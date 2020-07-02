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

Эти значения могут быть различны для каждого инстанса и задаются в Vagrantfile.

Provisioning инстансов производится с помощью Ansible,  а именно прописан в файлах playbook.yml и ролях.

Используя roles (Ansible) группируем задачи провизионинга, а именно:

base  - ставим необходимые программы и подключаем дополнительные репозитории
(во всех ролях есть механизм, какие программы и как ставить на инстанс в зависимости от используемой ОС)

java – устанавливает java 1.8.x JDK и java 11 

по дефолту устанавливается переменная JAVA_HOME = JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk

при запуске playbook  c ключом  ansible-playbook playbook.yml --extra-var "java=11"
устанавливается переменная JAVA_HOME = JAVA_HOME=/usr/lib/jvm/java-11-openjdk

selinux -  в этой роли Ansible отключает selinux

web-service – устанавливаем web_server Apache, копируем на него свою web-страничку и делаем так, чтоб он всегда стартовал при перезагрузке.

На страничке выводим специфичную для каждого инстанса информацию, взяв ее с Ansible. 

(Управление конфигурацией инстансов - редактирование Vagrantfile, провизионинг - редактирование ролей или добавление новых)



