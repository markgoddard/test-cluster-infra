===========================
Test Cluster Infrastructure
===========================

Ansible playbooks for testing clusters running on OpenStack.

Installation
============

Ensure that Ansible is installed, either via the system package manager or pip.
If required, use a virtualenv to avoid interference with the system python
packages. For example:

.. code-block:: console

   virtualenv venv
   source venv/bin/activate
   pip install -U pip
   pip install -r requirements.txt

Install Ansible role dependencies from Ansible Galaxy:

.. code-block:: console

   ansible-galaxy install \
       -p ansible/roles \
       -r requirements.yml

Configuration
=============

Edit the configuration file `etc/cluster-infra.yml` to configure the cluster
and the Ansible inventory that will be generated.

Usage
=====

First, ensure that OpenStack authentication environment variables are set,
typically by sourcing an OpenStack environment file.

To create a cluster:

.. code-block:: console

   ansible-playbook -i ansible/inventory -e @etc/cluster-infra.yml ansible/cluster-create.yml

To perform some basic checks on a cluster:

.. code-block:: console

   ansible-playbook -i ansible/inventory -e @etc/cluster-infra.yml ansible/cluster-check.yml

To destroy a cluster:

.. code-block:: console

   ansible-playbook -i ansible/inventory -e @etc/cluster-infra.yml ansible/cluster-destroy.yml
