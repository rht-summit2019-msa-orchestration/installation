#### ACME Ride Installation

This repository contains resources to install the Acme Ride app on OpenShift.

OCP version: 3.11

_Components:_
* Strimzi Kafka cluster
* Gogs
* PgAdmin4
* Jenkins
* Application Services

The repository contains the following folders:
* `ansible`: ansible playbooks and roles
* `openshift`: OpenShift templates and other resources

Ansible playbook installation order:
* strimzi_operator.yml (requires cluster admin rights)
* kafka_cluster.yml
* kafka_topics.yml
* gogs.yml
* pgadmin4.yml
* jenkins.yml
* jaeger.yml
* driver_service.yml
* passenger_service.yml
* dispatch_service.yml

Provisioning for user 'user1':
* Log into OpenShift cluster with admin user
* Install Strimzi operator
```
$ ansible-playbook playbooks/strimzi_operator.yml -e cluster_provisioner=user1
``` 
* Log into OpenShift cluster as user1
* Run Ansible playbooks:
```
$ ansible-playbook playbooks/kafka_cluster.yml
$ ansible-playbook playbooks/kafka_topics.yml
$ ansible-playbook playbooks/gogs.yml
$ ansible-playbook playbooks/pgadmin4.yml
$ ansible-playbook playbooks/jenkins.yml
$ ansible-playbook playbooks/jaeger.yml
$ ansible-playbook playbooks/driver_service.yml
$ ansible-playbook playbooks/passenger_service.yml
$ ansible-playbook playbooks/dispatch_service.yml
```