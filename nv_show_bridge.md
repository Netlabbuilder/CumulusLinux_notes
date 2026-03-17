### Reference Resources:
- [NVUE Command Reference](https://docs.nvidia.com/networking-ethernet-software/nvue-reference/Show-Commands/Bridge/)
### Examples:
- To show configuration settings for all the bridges on the switch, use `nv show bridge domain`
  ```
  cumulus@cumulus:mgmt:~$ nv show bridge domain 
  Domain      MAC address        Type        Encap   Ageing  Stp Mode  Vlan VNI Offset  Mcast Snooping
  ----------  -----------------  ----------  ------  ------  --------  ---------------  --------------
  br_default  48:b0:2d:04:f8:cf  vlan-aware  802.1Q  1800    rstp      0                disabled      
  cumulus@cumulus:mgmt:~$
  ```
- To show configuration settings for a specific bridge, use `nv show bridge domain <domain-id>`
  ```
  cumulus@cumulus:mgmt:~$ nv show bridge domain br_default 
  Bridge info: 
      mac-address         : 48:b0:2d:04:f8:cf
      type                : vlan-aware
      encap               : 802.1Q
      ageing              : 1800
      stp mode            : rstp
      vlan-vni-offset     : 0
  
  Bridge Vlan Info :
  untagged      tagged                                            
  ------------- ---------------------------------------------------
  1             100,200
  
  Bridge Port Info:
  Port           State           
  -------------- --------------- 
  swp32          forwarding      
  
  cumulus@cumulus:mgmt:~$
  ```
