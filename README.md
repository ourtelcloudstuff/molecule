# Test ansible role with molecule and Test Infra (using docker as molecule driver)


# Molecule
Molecule is designed to aid in the development and testing of Ansible roles including support for multiple instances, operating system distributions, virtualization providers and test frameworks.

# Test Infra

With Testinfra you can write unit tests in Python to test actual state of your servers configured by management tools like Salt, Ansible, Puppet, Chef and so on.

Testinfra aims to be a Serverspec equivalent in python and is written as a plugin to the powerful Pytest test engine

# Prerequisites 
Molecule test will launch docker to run ansible playbooks and Test infra, So docker must be install .

# Setup environment

Ubuntu

sudo apt-get update

python -m pip install virtualenv

python -m virtualenv molecule_env

source molecule_env/bin/activate

python -m pip install molecule docker

# Creating a Ansible Role in Molecule

$ molecule init role -r ansible-webhost -d docker

(The -r flag specifies the name of the role while -d specifies the driver, which provisions the hosts for Molecule to use in testing.)

$ cd ansible-apache


$ molecule test  (just to make sure molecule setup properly)


Configure task in Ansible role to make webhosting work

# Update Molecule as you per your requirement 

$ vim /ansible-webhost/molecule/default/molecule.yml

# Write the test cases 

$molecule/default/tests/test_default.py


httpd package should be install


httpd service should be up and running


Index.html file shoule be copied to /var/www/html


# Testing the Role with Molecule


(my_test) ourtelcloudthings@ubuntu:/etc/ansible$


(my_test) ourtelcloudthings@ubuntu:/etc/ansible$ cd roles/ansible-apache/


(my_test) ourtelcloudthings@ubuntu:/etc/ansible/roles/ansible-apache$ molecule test

