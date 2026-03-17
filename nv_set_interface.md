### Reference Resources:
- [NVUE Command Reference](https://docs.nvidia.com/networking-ethernet-software/nvue-reference/Set-and-Unset-Commands/Interface/)

### Examples:

- To set an IPv4 address for an interface, use `nv set interface <interface-id> ipv4 address <ip-prefix-id>`
  ```
  cumulus@cumulus:mgmt:~$ nv set interface lo ipv4 address 10.255.255.1/32
  created [rev_id: 2]
  cumulus@cumulus:mgmt:~$ nv config apply
  applied_and_saved [rev_id: 2]
  cumulus@cumulus:mgmt:~$ nv show interface lo ipv4 
                  operational      applied        
  --------------  ---------------  ---------------
  forward                          enabled        
  igmp                                            
    state                          disabled       
  dhcp-client                                     
    state                          disabled       
    set-hostname                   disabled       
  [address]       10.255.255.1/32  10.255.255.1/32
  [address]       127.0.0.1/8                     
  cumulus@cumulus:mgmt:~$ nv show interface lo ipv4 address 
  IPv4 Address     Address type
  ---------------  ------------
  10.255.255.1/32  primary     
  127.0.0.1/8      primary     
  cumulus@cumulus:mgmt:~$
  ```
