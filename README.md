# ansible-hands-on
## Ad-Hoc Commands (and demonstration)
* Check all my inventory hosts are ready to be managed by ansible
    $ ansible all -m ping
* Run the uptime command on all hosts in servers group
    $ ansible servers -m command -a "uptime"
    output -> 
        172.17.0.2 | CHANGED | rc=0 >>
        07:48:13 up  3:49,  1 user,  load average: 2.03, 2.17, 2.14
* collect and display the discovered for the localhost
  $ ansible localhost -m setup
<<<<<<< HEAD

## Inventory
- Inventory is a collection of hosts (nodes) against which can work with.
    * Hosts             * Inventory-specific data
    * Groups sources    * Static or Dynamic
- Ping to the host 
    * Ansible ad-hoc command:-
        ansible all -i hosts -u dark -m ping 

        output->
            172.17.0.2 | SUCCESS => {
            "ansible_facts": {
            "discovered_interpreter_python": "/usr/bin/python2.7"
            },
            "changed": false,
         "ping": "pong"
        }
- Gathering the facts
    * Ansible ad-hoc command:-
        ansible all -i hosts -u dark -m setup

- Installing Packages
    * Installing httpd
        ansible servers -i hosts -u dark -m apt -a "name=httpd state=present" -b --ask-become-pass
     * Removing httpd
        ansible servers -i hosts -u dark -m apt -a "name=httpd state=absent" -b --ask-become-pass
    
    # Introduction to Playbooks (and demonstration)
    ## Variable in Ansible
     - Variable:- 
        Ansible can work with metadata from various sources and manage their context in the form of variables.

    * Variables Example:-
        file: A directory should exit
        yum: A package should be installed
        service: A service should be running
        templates: Render a config file from a template
        get_url: Fetch an archive file from a URL
        git: Clone the source code repository
    ## Handler Tasks
        * Handler are special tasks that run at the end of a play if notfied by another task

        if a configuration files gets changed notify a service restart task it needs to run.

