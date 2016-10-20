[![Build Status](https://travis-ci.org/lae/ansible-role-dse_repo.svg?branch=master)](https://travis-ci.org/lae/ansible-role-dse_repo)
[![Galaxy Role](https://img.shields.io/badge/ansible--galaxy-dse_repo-blue.svg)](https://galaxy.ansible.com/lae/dse_repo/)

lae.dse_repo
=========

Configures the Datastax Enterprise repository, either the official one or a
mirror (e.g. onsite mirror behind a firewall).

Role Variables
--------------

    # Set to true if using a mirror
    dse_repo_is_mirror: false
    # Abbreviated fingerprint of the public key used to sign packages on the mirror
    dse_repo_mirror_key_id: B999A372
    # Full URI to the mirror
    dse_repo_mirror_uri: "http://packages.local/aptly/dse"
    # Set the following to your DSE username/password to use official repos
    dse_repo_user: john.doe
    dse_repo_password: hunter2

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
        dse_repo_user: localuser
        dse_repo_password: hunter2
        dse_repo_mirror_uri: "https://{{ dse_repo_user }}:{{ dse_repo_password }}@packages.local/aptly/dse"

...and include the public key used to sign the packages in the mirror in
`files/datastax_apt_mirror_key.asc` (and `files/datastax_rpm_mirror_key.asc`
for RHEL/CentOS) in your playbook's directory. (Note, you don't *need* to use
the `dse_repo_user|password` variables there.)

License
-------

MIT

nothing really
