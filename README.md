# monasca-default-alarms

This role will setup a default alarm definition configuration for Monasca.

##Requirements
This role utilizes the Monasca modules found at https://github.com/hpcloud-mon/ansible-module-monasca

It is assumed the service endpoint for Monasca is properly registered in keystone.

##Role Variables

These variables must be defined.

- keystone_url
- keystone_user
- keystone_password

By default the configured alarms will be setup with a notification to root@localhost change the `default_email` variable to modify.

##Example Playbook

    - name: Define default alarms
      hosts: mini-mon
      gather_facts: no
      vars:
        keystone_url: http://192.168.10.5:35357/v3/
        keystone_user: mini-mon
        keystone_password: password
      roles:
        - {role: monasca-default-alarms, tags: [alarms]}

## Modules included in Library
The library directory is for Ansible modules used by this project.

The modules are maintained in a separate git repo and added here using
[git-subtree](https://github.com/git/git/blob/master/contrib/subtree/git-subtree.txt). For example to setup initially:

    git subtree add --prefix library https://github.com/hpcloud-mon/ansible-module-monasca.git master --squash

Then to update:

    git subtree pull --prefix library https://github.com/hpcloud-mon/ansible-module-monasca.git master --squash


##License
Apache

##Author Information
Tim Kuhlman
Monasca Team email monasca@lists.launchpad.net
