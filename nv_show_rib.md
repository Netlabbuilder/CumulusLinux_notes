### Reference Resources:

- [NVUE Command Reference](https://docs.nvidia.com/networking-ethernet-software/nvue-reference/Show-Commands/RIB/)

### Examples:

- To view the router's per vrf routing table (IPv4 and IPv6), run `nv show vrf <vrf-id> router rib`:
  
  ```
  cumulus@spine1:mgmt:~$ nv show vrf default router rib
  AFI   Prefix           
  ----  -----------------
  ipv4  172.16.1.0/31    
        172.16.1.0/32    
        172.16.1.2/31    
        172.16.1.2/32    
        172.16.1.4/31    
        172.16.1.4/32    
        172.16.1.6/31    
        172.16.1.6/32    
        172.16.2.0/31    
        172.16.2.2/31    
        172.16.2.4/31    
        172.16.2.6/31    
        172.16.255.1/32  
        172.16.255.2/32  
        172.16.255.3/32  
        172.16.255.4/32  
        172.16.255.253/32
        172.16.255.254/32
  ipv6  fe80::/64        
  cumulus@spine1:mgmt:~$
  ```
- To view IPv4 or IPv6 routing table of a specific VRF, run `nv show vrf <vrf-id> router rib <afi>`
  ```
  cumulus@spine1:mgmt:~$ nv show vrf default router rib ipv4
                operational  applied
  ------------  -----------  -------
  fib-filter                        
    route-map   none                
    [protocol]                      
  
  
  
  route
  ========
  
      Flags - * - selected, q - queued, o - offloaded, i - installed, S - fib-selected, x - failed
  
      Route              Protocol   Distance  ResolvedVia  ResolvedViaIntf  Uptime   NHGId  Metric  TableId  Flags
      -----------------  ---------  --------  -----------  ---------------  -------  -----  ------  -------  -----
      172.16.1.0/31      connected  0                                       1:54:18  17     0                *Si  
                         ospf       110                                     1:54:17  35     100                   
      172.16.1.0/32      local      0                                       1:54:18  17     0                *Si  
      172.16.1.2/31      connected  0                                       1:54:18  18     0                *Si  
                         ospf       110                                     1:54:17  36     100                   
      172.16.1.2/32      local      0                                       1:54:18  18     0                *Si  
      172.16.1.4/31      connected  0                                       1:54:18  19     0                *Si  
                         ospf       110                                     1:54:17  37     100                   
      172.16.1.4/32      local      0                                       1:54:18  19     0                *Si  
      172.16.1.6/31      connected  0                                       1:54:18  20     0                *Si  
                         ospf       110                                     1:54:17  38     100                   
      172.16.1.6/32      local      0                                       1:54:18  20     0                *Si  
      172.16.2.0/31      ospf       110                                     1:52:37  40     200              *Si  
      172.16.2.2/31      ospf       110                                     1:48:53  45     200              *Si  
      172.16.2.4/31      ospf       110                                     1:48:03  54     200              *Si  
      172.16.2.6/31      ospf       110                                     1:47:33  65     200              *Si  
      172.16.255.1/32    ospf       110                                     1:52:37  40     100              *Si  
      172.16.255.2/32    ospf       110                                     1:48:53  45     100              *Si  
      172.16.255.3/32    ospf       110                                     1:48:03  54     100              *Si  
      172.16.255.4/32    ospf       110                                     1:47:33  65     100              *Si  
      172.16.255.253/32  connected  0                                       1:54:18  15     0                *Si  
                         local      0                                       1:54:18  15     0                i    
                         ospf       110                                     1:54:17  30     0                     
      172.16.255.254/32  ospf       110                                     1:47:33  66     200              *Si  
  cumulus@spine1:mgmt:~$ nv show vrf default router rib ipv6
                operational  applied
  ------------  -----------  -------
  fib-filter                        
    route-map   none                
    [protocol]                      
  
  
  
  route
  ========
  
      Flags - * - selected, q - queued, o - offloaded, i - installed, S - fib-selected, x - failed
  
      Route      Protocol   Distance  ResolvedVia  ResolvedViaIntf  Uptime   NHGId  Metric  TableId  Flags
      ---------  ---------  --------  -----------  ---------------  -------  -----  ------  -------  -----
      fe80::/64  connected  0                                       1:54:21  22     0                i    
                 connected  0                                       1:54:21  23     0                i    
                 connected  0                                       1:54:21  24     0                i    
                 connected  0                                       1:54:21  25     0                *Si  
  cumulus@spine1:mgmt:~$
  ```
