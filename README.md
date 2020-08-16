Тестовое задание

Box в Vagrant ubuntu/xenial64, хосты:
balancer 10.124.0.2
front1 10.124.0.3
front2 10.124.0.4
back 10.124.0.5
elk 10.124.0.6
controller 10.124.0.17
Лимиты RAM по 512 Мб, elk - 4 Гб
Port forwarding - localhost:8083 -> balancer:80 (точка входа http)
localhost:8084 -> elk:5601 (kibana)
HTML файл лежит на хосте back в /var/www/html/index.nginx-debian.html
HTTP трафик заходит на balancer, проксируется на front1/front2 и далее на back
Логи nginx читаются filebeat'ом и отправляются в logstash на хосте ELK, далее идут в Elasticsearch
В Kibana необходимо после запуска настроить индексы
Ansible запускается на хосте controller
