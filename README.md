[![Build Status](https://travis-ci.org/lae/ansible-role-dse_repo.svg?branch=master)](https://travis-ci.org/lae/ansible-role-dse_repo)
[![Galaxy Role](https://img.shields.io/badge/ansible--galaxy-dse_repo-blue.svg)](https://galaxy.ansible.com/lae/dse_repo/)

lae.dse_repo
=========

Configures the Datastax Enterprise repository, either the official one or a
mirror (e.g. onsite mirror behind a firewall).

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Example Playbook
----------------

Using the official repository:

    - hosts: dse01
      roles:
        - lae.dse_repo
      vars:
        dse_repo_user: john.doe
        dse_repo_password: hunter2

Using a password-protected mirror of the official repository:

    - hosts: dse01
      roles:
        - lae.dse_repo
      vars:
        dse_repo_is_mirror: true
        dse_repo_mirror_key_id: FB72CC01
        dse_repo_mirror_uri: "https://localuser:password123@packages.local/aptly/dse"

...and include the public key used to sign the packages in the mirror in
`files/datastax_mirror_key.asc` in your playbook's directory.

License
-------

MIT
