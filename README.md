Role Name
=========

Ansible Sonatype Nexus role. Completely independent from any package manager.
Does not require root or sudo permission to run.

TODO
----
- Add datadir (plus entry nexus-work={{datadir}} in conf/nexus.properties
- Change default admin account (admin/admin123)


Role Variables
--------------

- **nexus_download_dir**: download path on the control machine that will be used. Defaults to *'/tmp'*
- **nexus_version**: Nexus version to be installed. Defaults to *'latest'*
- **nexus_installation_dir**: installation prefix that will be used on installation hosts. Defaults to *'/usr/share'*
- **nexus_work_dir**: working directory, aka sonatype-work
- **nexus_port**: TCP port
- **nexus_manage_os_user**: Boolean value which controls whether the nexus o/s user is managed by the Playbook. Defaults to true.
- **nexus_os_user**: The name of the nexus o/s user to create/ manage when ``nexus_manage_os_user`` is true. Defaults to 'nexus'.
- **nexus_manage_os_group**: Boolean value which controls whether the nexus o/s group is managed by the Playbook. Defaults to the value of ``nexus_manage_os_user``.
- **nexus_os_group**: The name of the nexus o/s group to create/ manage when ``nexus_manage_os_group`` is true. Defaults to 'nexus'.
- **nexus_os_user_shell**: The shell to set for the nexus user. Only effective when when ``nexus_manage_os_user`` is true. Defaults to '/bin/bash'
- **nexus_properties**: A dict containing key/ value pairs to be written in to ``nexus.properties``. By default this will contain the keys/values specified in ``defaults/main.yml``, however this can be overridden to contain arbitrary keys/values. Note: Ansible does not merge dicts by default so if you provide *any* keys/values then the ones in ``defaults/main.yml`` will not be used and must be re-specified in your dict to be included, (unless you have switched on [hash merging][1] of course). If you re-implement this dict with custom values you _must_ specify a value for the ``nexus-work`` key, even if you stick to the default location. 

Dependencies
------------

wget (on host, not on clients)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: jhinrichsen.nexus, nexus_installation_dir: '/opt' }

License
-------

MIT

Author Information
------------------

This playbook is heavily inspired by Alexander Ramos Jardim.
Any errors are probably my fault.

[1]: http://docs.ansible.com/intro_configuration.html#hash-behaviour