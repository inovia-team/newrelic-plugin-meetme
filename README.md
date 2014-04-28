newrelic-plugin-meetme
========

This role is responsible for installing the [newrelic-plugin-agent](https://github.com/MeetMe/newrelic-plugin-agent)

It will be capable of monitoring the following services:

- Alternative PHP Cache
- Apache HTTP Server
- CouchDB
- Elasticsearch
- HAProxy
- Memcached
- MongoDB
- Nginx
- pgBouncer
- PHP FPM
- PostgreSQL
- RabbitMQ
- Redis
- Riak
- uWSGI


Requirements
------------

Users must have a valid NewRelic account and provide a valid newrelic_license_key

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    newrelic_license_key: DEFINE_WITH_YOUR_OWN_KEY

Your NewRelic license key must be set for this role to operate properly.

    newrelic_plugin_agent_version: latest

Specify either `latest` or a specific version number to install via pip

    newrelic_plugin_poll_interval: 60

The rate at with the agent will poll to NewRelic

    #newrelic_plugin_api_timeout: 10
    #newrelic_proxy: http://localhost:8080

These two variables are not set by default however they can be specified to force their inclusion.

    newrelic_plugin_user: newrelic

The user the newrelic_plugin_agent should run as.

    newrelic_plugin_config_location: /etc/newrelic
    newrelic_plugin_config_name: newrelic_plugin_agent.cfg

The location and name for the config file. The config location will be created and chowned to the `newrelic_plugin_user`

    newrelic_plugin_daemon_location: /usr/local/bin
    newrelic_plugin_daemon_name: newrelic_plugin_agent

The location of the installed service. This differs by OS. Debian will install to `/usr/local/bin/` where RedHat will install to `/usr/bin`

    newrelic_plugin_log_location: /var/log/newrelic
    newrelic_plugin_log_name: newrelic_plugin_agent.log

The location and name for the log

    newrelic_plugin_log_format: '%(levelname) -10s %(asctime)s %(process)-6d %(processName) -15s %(threadName)-10s %(name) -25s %(funcName) -25s L%(lineno)-6d: %(message)s'
    newrelic_plugin_log_maxbytes: 10485760
    newrelic_plugin_log_backupcount: 3
    newrelic_plugin_log_level: INFO
    newrelic_plugin_log_propagate: True

Overide these to change the default behavior of the logging of the agent. (See `templates/newrelic_plugin_agent.cfg.j2`)

    newrelic_plugin_pid_location: /var/run/newrelic
    newrelic_plugin_pid_name: newrelic_plugin_agent.pid

The location and name for the pid

    newrelic_plugin_apache: False
    newrelic_plugin_couchdb: False
    newrelic_plugin_elasticsearch: False
    newrelic_plugin_haproxy: False
    newrelic_plugin_mongodb: False
    newrelic_plugin_memcached: False
    newrelic_plugin_nginx: False
    newrelic_plugin_pgbouncer: False
    newrelic_plugin_php_apc: False
    newrelic_plugin_php_fpm: False
    newrelic_plugin_postgresql: False
    newrelic_plugin_rabbitmq: False
    newrelic_plugin_redis: False
    newrelic_plugin_riak: False

All of the available services that can be monitored. (See `templates/newrelic_plugin_agent.cfg.j2` for all required variables for each service)

Dependencies
------------

There are no external dependencies.

Example Playbook
-------------------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: Rackspace_Automation.newrelic_plugin_meetme, newrelic_license_key: YOUR_LICENSE_KEY }

License
-------

BSD

Author Information
------------------

Bruce Stringer <bruce.stringer@rackspace.com>

Additional Information
----------------------

This role is not yet production ready.


[Rackspace - the open cloud company](http://rackspace.com)
Ask about our DevOps Automation Service - [www.rackspace.com/devops](http://rackspace.com/devops)