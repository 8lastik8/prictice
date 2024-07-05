# Slurm Hell Practice
 
Репозиторий сделан для практики написания плейбука с ролями для Ansible

Тестировался на Ubuntu22

Для работы плейбука необходимо установить:
community.postgresql
``` ansible-galaxy collection install community.postgresql ```

Старался максимально лаконично формировать содержимое roles но можно потеряться, поэтому сделаю оглавление:

1. app: 
    - files: ->  файлы самого приложения
    - handlers: -> для перезапуска systemd
    - tasks: -> для main.yml
    - templates: -> app и env
2. nginx: 
    - files: -> nginx.conf (планировал затолкать в templates но что-то пошло не так и забыл)
    - tasks: -> main.yml
3. postgresql:
    - handlers: -> main.yml
    - meta: -> для явного указания очередности, так как все зависимости устанавливаются в роли services
    - tasks: -> main.yml (сделан колхозно но своё)
4. services:
    - tasks: -> main.yml ( установка базовых зависимостей)

Всё запускалось на ansible [core 2.12.10]
