- To show current running Cumulus Linux release/build, hostname, uptime and timezone, use `nv show system`:

  ```
  cumulus@cumulus:mgmt:~$ nv show system
                     operational          applied
  -----------------  -------------------  -------
  uptime             0:12:11                     
  hostname           cumulus              cumulus
  fqdn               cumulus                     
  product-name       Cumulus Linux               
  contact                                        
  location                                       
  dns                                            
    domain                                       
  date-time                                      
    local-time       2026-03-07 15:08:02         
    timezone         Etc/UTC              Etc/UTC
  health                                         
    status           Not OK                      
  version                                        
    product-release  5.16.0                      
  global                                         
    system-mac       48:b0:2d:d5:f1:93    auto   
    anycast-mac      none                 none
  ```
  
- To show current system version use `nv show system version`:

  ```
  cumulus@cumulus:mgmt:~$ nv show system version 
                   operational                 
  ---------------  ----------------------------
  onie             N/A                         
  kernel           6.1.0-cl-1-amd64            
  base-os          Debian GNU/Linux 12.13      
  product-release  5.16.0                      
  image                                        
    build-id       5.16.0.0087                 
    build-date     Thu Feb 19 20:27:27 UTC 2026
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
