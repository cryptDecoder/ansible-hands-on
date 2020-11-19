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

## Variable in Ansible
    * Variable:- 
        Ansible can work with metadata from various sources and manage their context in the form of variables.
=======
>>>>>>> 1de30e2df730b5766a6066a9fb6fb01feb17afd9
