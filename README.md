vagrant_jenkins
=======================

Be sure to `git clone --recursive ` for the submodules!


This will setup a vagrant virtual instance and portforward 8080 to 8888 on your host.
Ansible will be called and using the included Ansible Roles (`geerlingguy/java`, `geerlingguy/ansible-role-jenkins`, `geerlingguy/ansible-role-firewall`) you will get a running Jenkins instance.

Try it!

    vagrant up jenkins --provision
    curl http://localhost:8888

Creds:

    username: admin
    password: admin
