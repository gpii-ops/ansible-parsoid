Parsoid
============

Installs and configures a Parsoid instance, using the nodejs role.

Most of the work to install the Parsoid itself is done through passing appropriate defaults to the `ansible-nodejs` role; this role completes the installation of Parsoid done by ansible-nodejs role.

- Installs addtional local npm packages
- Configures the file localsettings.js

Requirements
------------

- The application is self-contained and doesn't have external dependencies

Role Variables
--------------

- `parsoid_domains`: List of dictionaries with the domain and the uris of the mediawiki applications that will use the instance of Parsoid.

Dependencies
------------

- https://github.com/idi-ops/ansible-facts
- https://github.com/idi-ops/ansible-nodejs

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    ---
    
    - hosts: all
      sudo: true
    
      vars:
        nodejs_app_name: parsoid
        nodejs_app_install_dir: /opt/{{ nodejs_app_name }}
        nodejs_app_git_repo: https://github.com/wikimedia/parsoid.git
        nodejs_app_git_branch: master
        nodejs_app_commands: {}
        nodejs_app_start_script: "bin/server.js"
        nodejs_app_host_address: 127.0.0.1
        nodejs_app_tcp_port: 8000
        nodejs_app_test_http_endpoint: /
        nodejs_app_test_http_status_code: 200
        nodejs_app_test_string: "<h3>Welcome to the <a"
        
        parsoid_domains:
          - domain: "localhost"
            uri: "http://localhost/w/api.php"
        
      roles:
        - ansible-facts
        - ansible-nodejs
        - ansible-parsoid

License
-------

MIT.

Author Information
------------------
