Schibsted.appmgr-app
====================
A role for installing appmgr applications.

Requirements
------------
Installation of appmgr.
There is a PPA for ubuntu here: https://launchpad.net/~appmgr/+archive/ubuntu/main

appmgr uses curl and if you need to specify a username and password for your maven needs, you
need to specify a .netrc in the home folder of the user. This file is typically '/opt/apps/.netrc'.

Role Variables
--------------

```
ec2_enabled:
  Flag for enabling collection of ec2_facts.

stackdriver_api_key:
  Enables stackdriver, to publish the artifact being installed.

app:
  This is an object which MUST be filled out with the following keys.

  name: 
    Directory name which the application will be installed under. 
    Should not contain spaces.

  groupId: 
    Maven group Id

  artifactId: 
    Maven artifactId

  classifier: 
    Maven classifier (defaults to 'appmgr'). May be set to '' to have no classifier

  version: 
    Maven version

  enabled:
    If the application should be enabled or not.

  config: 
    List of name value pairs of configuration that will be sent to 'app conf'.

  environment: 
    List of name/value pairs that will be entered into 
    '{{app_home}}/{{app.name}}/environment'.
    This file should be sourced by the launcher script of the app.


upgrade:
  If the application exists, this variable signals if the application should be updated or not.

app_user:
  The user which owns the application. This is also the user which runs the application. Defaults to 'app'

app_group:
  The group which owns the application. This is also the user which runs the application. Defaults to 'app'

maven_repository:
  The maven repository which the application will be downloaded from.

app_home:
  The base directory for the applications. Defaults to '/opt/apps'

```

Dependencies
------------
- Schibsted.monit

Example Playbook
-------------------------

See the sample-playbook.yml in the git repository.

License
-------

MIT

Author Information
------------------

* Erlend Hamnaberg (github.com/hamnis, twitter.com/hamnis)
* Jordi Arnavat (github.com/acjzz, twitter.com/acjzz)
