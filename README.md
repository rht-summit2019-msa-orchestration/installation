#### ACME Ride Installation

This repository contains resources to install the Acme Ride app on OpenShift.

OCP version: 3.11

_Components:_
* Strimzi Kafka cluster
* Gogs

The repository contains the following folders:
* `ansible`: ansible playbooks and roles
* `openshift`: OpenShift templates and other resources

Ansible playbook installation order:
* strimzi_operator.yml (requires cluster admin rights)
* kafka_cluster.yml
* kafka_topics.yml
* gogs.yml
