- To show current running Cumulus Linux release/build, hostname, uptime and timezone, use `nv show system`:

  ```
  cumulus@cumulus:mgmt:~$ nv show system 
            operational          applied
  --------  -------------------  -------
  hostname  cumulus              cumulus
  build     Cumulus Linux 5.6.0         
  uptime    1:57:42                     
  timezone  Etc/UTC                     
  cumulus@cumulus:mgmt:~$
  ```
- To change hostname, use `nv set system hostname <hostname>`. The following example is to change the hostname from `cumulus` to `spine-1`. However, the new hostname is in `pending` state:

  ```
  cumulus@cumulus:mgmt:~$ nv set system hostname spine-1
  cumulus@cumulus:mgmt:~$ nv show system
            operational          applied  pending
  --------  -------------------  -------  -------
  hostname  cumulus              cumulus  spine-1
  build     Cumulus Linux 5.6.0                  
  uptime    2:00:23                              
  timezone  Etc/UTC                              
  cumulus@cumulus:mgmt:~$
  ```
- To apply new changes, use `nv config apply`:

  ```
  cumulus@cumulus:mgmt:~$ nv config apply
  cumulus@cumulus:mgmt:~$ nv show system 
            operational          applied
  --------  -------------------  -------
  hostname  spine-1              spine-1
  build     Cumulus Linux 5.6.0         
  uptime    2:09:33                     
  timezone  Etc/UTC                     
  cumulus@cumulus:mgmt:~$
  ```
