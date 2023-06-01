# lmk8s (s053278)
## Задание

**Цель:** Закрепление материала полученного в пройденных курсах, знакомство с установкой и использование систем мониторинга и логирования за пределами Kubernetes, получение практического опыта работы с конфигурацией Prometheus и Fluentbit.

**Результат:** Набор Ansible ролей для установки и конфигурации Prometheus и его экспортеров, а так же стека логирования EFK.
Репозиторий на Github.com с ролями и плейбуками Ansible.

**Задание:** Необходимо подготовить Ansible роли для разворачивания Prometheus (вне кластера Kubernetes, для мониторинга внешних хостов), для установки Node exporter и добавления static config в конфигурацию развернутого Prometheus с новым хостом, разворачивания ElasticSearch + Kibana, установки fluentbit с настроенным сбором системных логов (из journald) в установленный ElasticSearch.

## Системные требования
Elasticsearch требователен к железу.

Необходимо:
- vCPU: 4
- Memory: 8192 mb

## Установка
Здесь описан способ установки Prometheus и стека EFK

### Подготовка
Необходимо установить ansible => 2.11 (требуется для работы модуля **ansible.builtin.meta**)
```
pip3 install -r requirements.txt
```
Перед установкой ElasticSearch/Kibana необходимо скачать *.deb и/или *.rpm пакеты и указать пути к ним в **group_vars**

### Запуск плейбука
Плейбук необходимо запустить командой:
```
ansible-playbook install.yml
```

**Допустимые теги:**
```
ansible-playbook install.yml -t prometheus
ansible-playbook install.yml -t node_exporter
ansible-playbook install.yml -t elastic
ansible-playbook install.yml -t fluentbit
```

## Доступы
- Prometheus доступен по ссылке http://localhost:9090/
- Node Exporter доступен по ссылке http://localhost:9100/
- ElasticSearch доступен по ссылке http://localhost:9200/
- Kibana доступен по ссылке http://localhost:5601/