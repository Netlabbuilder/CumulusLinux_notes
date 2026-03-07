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
- To change hostname, use `nv set system hostname <hostname>`. The following example is to change the hostname from `cumulus` to `Leaf-1`. However, the new hostname is in `pending` state:

  ```
  cumulus@cumulus:mgmt:~$ nv set system hostname Leaf-1
  created [rev_id: 2]
  cumulus@cumulus:mgmt:~$
  cumulus@cumulus:mgmt:~$ nv show system
                     operational          applied  pending
  -----------------  -------------------  -------  -------
  uptime             0:35:06                              
  hostname           cumulus              cumulus  Leaf-1 
  fqdn               cumulus                              
  product-name       Cumulus Linux                        
  contact                                                 
  location                                                
  dns                                                     
    domain                                                
  date-time                                               
    local-time       2026-03-07 15:30:58                  
    timezone         Etc/UTC              Etc/UTC  Etc/UTC
  health                                                  
    status           Not OK                               
  version                                                 
    product-release  5.16.0                               
  global                                                  
    system-mac       48:b0:2d:d5:f1:93    auto     auto   
    anycast-mac      none                 none     none   
  cumulus@cumulus:mgmt:~$
  ```
- To apply new changes, use `nv config apply`. The new hostname is in `applied` state. To see the new hostname, logout and login again: 

  ```
  cumulus@cumulus:mgmt:~$ nv config apply
  Warning: current hostname `cumulus` will be replaced with `Leaf-1`
  
  Are you sure? [y/N] y
  applied_and_saved [rev_id: 2]
  cumulus@cumulus:mgmt:~$
  cumulus@cumulus:mgmt:~$ nv show system
                       operational          applied
  -----------------  -------------------  -------
  uptime             0:38:18                     
  hostname           Leaf-1               Leaf-1 
  fqdn               Leaf-1                      
  product-name       Cumulus Linux               
  contact                                        
  location                                       
  dns                                            
    domain                                       
  date-time                                      
    local-time       2026-03-07 15:34:10         
    timezone         Etc/UTC              Etc/UTC
  health                                         
    status           Not OK                      
  version                                        
    product-release  5.16.0                      
  global                                         
    system-mac       48:b0:2d:d5:f1:93    auto   
    anycast-mac      none                 none   
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
  cumulus@cumulus:mgmt:~$ exit
  logout
  
  Debian GNU/Linux 12 Leaf-1 ttyS0
  
  Leaf-1 login: cumulus
  Password: 
  Linux Leaf-1 6.1.0-cl-1-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.123-1+cl5.16.0u7 (2026-01-25) x86_64
  Welcome to NVIDIA Cumulus (R) Linux (R)
  For support and online technical documentation, visit https://www.nvidia.com/en-us/support
  The registered trademark Linux (R) is used pursuant to a sublicense from LMI, the exclusive licensee of Linus Torvalds, owner of the mark on a world-wide basis.
  Last login: Sat Mar  7 15:05:47 UTC 2026 on ttyS0
  Number of total successful connections since last 1 days: 1
  
    "last_reboot_cause": "Unknown".
  
  ZTP in progress. To disable, do 'ztp -d'
  
  cumulus@Leaf-1:mgmt:~$ 
  cumulus@Leaf-1:mgmt:~$ 
  ```
