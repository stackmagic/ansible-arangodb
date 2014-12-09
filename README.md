arangodb
========

Installation and limited configuration of the [triAGENS ArangoDB](https://www.arangodb.com) Multi-Model NoSQL Database.

Requirements
------------

A Debian `6.x`, `7.x` or `testing` system. Other platforms are not (yet) supported. Feel free to fork-hack-pullrequest.

Role Variables
--------------

For basic operation, you only need to know about 2 variables:

* `arangodb_version` defines the version to be installed. Using `*` is possible but discouraged since arangodb requires to run a [manual upgrade](https://docs.arangodb.com/Installing/Upgrading.html) when installing a newer version so upgrading should be supervised by a human.
* `arangodb_autoupgrade` allows you to disregard the warning above and let the role invoke upgrade whenever a new version have been installed.

To customize anything inside `/etc/arangodb/arangod.conf` please refer to [templates/arangod.conf.j2](templates/arangod.conf.j2) and [defaults/main.yml](defaults/main.yml).

Other config files cannot be customized at this time.

Dependencies
------------

This role installs `apt-transport-https` on `debian` to fetch packages via https.

Example Playbook
----------------

To just install and run arangodb out-of-the-box, select your version and that's it:

    - hosts: servers
      roles:
         - { role: stackmagic.arangodb, arangodb_version: '2.3.1' }

To customize more settings

TODO
----

* customize user/group (arangodb automatically sets up a user and group when installing their package already)
* configure more settings (cluster and other config files)
* maybe create databases/collections
* add more platforms besides debian 6/7/testing

Author Information
------------------

github: [stackmagic](https://github.com/stackmagic)
