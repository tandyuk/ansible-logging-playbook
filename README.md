ansible-logging-playbook
========================

Ansible playbook containing a logging/monitoring system for pfsense, vmware esxi cluster, scopserv pbx and cpanel cluster using Logstash, Packetbeat, Redis, Elasticsearch, Kibana, Nfsen, and Observium.


Assumptions:

Your 'aggregator' node is a dedicated machine (or vm) running debian.
Your 'dns-servers' are cPanel DNSonly machines running centos 5 or 6.
Your 'voip-servers' are Scopserv pbxes runnign centos 5.x
Your 'cpanel-servers' are cPanel machines running centos 6.x
You will execute the playbook on the 'aggregator' host.
You have created ssh keys for your user on the aggregator host, and added these to /root/ssh/authorized_keys on each of the other hosts.
You have created an ssl crt/key pair on the aggregator, and saved these as /etc/ssl/certs/lumberjack.crt and /etc/ssl/private/lumberjack.key. You place a copy of your own lumberjack.crt in roles/logstash/templates/


As I develop this logging system, it will start very much tuned to my exact setup.
Over time I hope to move the majority of 'my setup' to hosts and site.yml so that this is easily customisable and deployable for others.

Feel free to use my templates etc, but if they save you lots of time and effort, please thank me for that by donating!
BTC: 1P18NPpcYdAVsFfSfr823x6R73KtFipkbN
