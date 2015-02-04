ansible-logging-playbook
========================

Ansible playbook containing a logging/monitoring system for pfsense, vmware esxi cluster, scopserv pbx and cpanel cluster using Logstash, Packetbeat, Redis, Elasticsearch, Kibana, Nfsen, and Observium.


Assumptions
===========
Your 'aggregator' node is a dedicated machine (or vm) running debian **x86**.

Your 'dns-servers' are cPanel DNSonly machines running centos 5.x or 6.x, or cloudlinux 6.x

Your 'voip-servers' are Scopserv pbxes runnign centos 5.x

Your 'cpanel-servers' are production cPanel machines running centos or cloudlinux 6.x

Your 'cpanel-dev-servers' are development cPanel machines running centos or cloudlinux 6.x with packetbeat

You will execute the playbook on the 'aggregator' (debian) host.

You have created ssh keys for your user on the aggregator host, and added these to /root/.ssh/authorized_keys on each of the other hosts.

You have created an ssl crt/key pair on the aggregator, and saved these as /etc/ssl/certs/lumberjack.crt and /etc/ssl/private/lumberjack.key. You place a copy of your own lumberjack.crt in roles/logstash/templates/

Pre-requisites
==============
On your Aggregator host:

apt-get install python-pip python-dev git sudo

pip install PyYAML jinja2 paramiko

git clone https://github.com/ansible/ansible.git

cd ansible

make install


Finally,

visudo

and add a line similar to

youruser   ALL=(ALL:ALL) ALL

replacing youruser with the username of the unpriviledged account you created during debian setup.


About
=====
As I develop this logging system, it will start very much tuned to my exact setup.

Recently I have moved the logstash configs to a more defined format for the aggregator host:

1?-xxxxx.conf:  Define local file (and other) inputs, for logging the local system.

2?-xxxxx.conf: Define inputs for logging from remote systems.

Both these sets of inputs are expected to set a type on the input, which will then match the relevant

3?-xxxxx.conf: Define filters for certain formats.

Big gap for future changes

9?-xxxxx.conf: Define outputs.



Over time I hope to move the majority of 'my setup' to hosts and site.yml so that this is easily customisable and deployable for others.


Share & Donate
==============
Feel free to use and share my templates etc, but if they save you lots of time and effort, please thank me for that by donating!

BTC: 1P18NPpcYdAVsFfSfr823x6R73KtFipkbN
Paypal: admin@tandyukservers.co.uk
