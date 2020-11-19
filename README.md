# ansible-hands-on
## Ad-Hoc Commands (and demonstration)
* Chech all my inventory hosts are ready to be managed by ansible
    $ ansible all -m ping
* Run the uptime command on all hosts in servers group
    $ ansible servers -m command -a "uptime"
    output -> 
        172.17.0.2 | CHANGED | rc=0 >>
        07:48:13 up  3:49,  1 user,  load average: 2.03, 2.17, 2.14
* collect and display the discovered for the localhost
  $ ansible localhost -m setup