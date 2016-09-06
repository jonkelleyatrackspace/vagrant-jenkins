vagrant_jenkins
=======================

Be sure to `git clone --recursive ` for the submodules!


This will setup a vagrant virtualinstane and portforward 8080 to 8888 on your localmachine.
Ansible will be called and using the included Ansible Roles (`geerlingguy/java`, `geerlingguy/ansible-role-jenkins`, `geerlingguy/ansible-role-firewall`) to deploy a running Jenkins instance.

    vagrant up jenkins --provision
    curl http://localhost:8888
