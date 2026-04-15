
```
cumulus@leaf1:mgmt:~$ nv show evpn
                       operational   applied      
---------------------  ------------  -------------
state                                enabled      
route-advertise                                   
  nexthop-setting                    system-ip-mac
  svi-ip               disabled      disabled     
  default-gateway      disabled      disabled     
dad                                               
  state                enabled       enabled      
  mac-move-threshold   5             5            
  move-window          180           180          
  duplicate-action     warning-only  warning-only 
[vni]                                             
multihoming                                       
  state                              disabled     
  mac-holdtime         1080                       
  neighbor-holdtime    1080                       
  startup-delay        180                        
  startup-delay-timer  --:--:--                   
  uplink-count         0                          
  uplink-active        0                          
l2vni-count            1                          
l3vni-count            1                          
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show evpn vni

NumMacs - Number of MACs (local and remote) known for this VNI, NumArps - Number
of ARPs (IPv4 and IPv6, local and remote) known for this VNI , NumRemVteps -
Number of Remote Vteps, Bridge - Bridge to which the vni belongs, Vlan - VLAN
assoicated to MAC

VNI  NumMacs  NumArps  NumRemVteps  TenantVrf  Bridge      Vlan
---  -------  -------  -----------  ---------  ----------  ----
10   2        2        1            SERVICE_A  br_default  10  
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show evpn vni 10
                   operational   applied
-----------------  ------------  -------
route-advertise                         
  svi-ip           disabled             
  default-gateway  disabled             
route-target                            
  [both]           65001:10             
[remote-vtep]      172.16.255.2         
vlan               10                   
bridge-domain      br_default           
tenant-vrf         SERVICE_A            
vxlan-interface    vxlan48              
mac-count          2                    
host-count         2                    
remote-vtep-count  1                    
local-vtep         172.16.255.1         
cumulus@leaf1:mgmt:~$
```

```
cumulus@leaf1:mgmt:~$ nv show vrf evpn 

State - State of the L3VNI, Svi - Svi interface for L3VNI, RouterMac - Router
MAC Address, SystemMac - System MAC Address, NexthopCount - Number of ARPs (IPv4
and IPv6, local and remote) known for this VNI, RouterMacCount - Number of MACs
(local and remote) known for this VNI, VXLANIntf - Vxlan interface of the L3VNI,
PrefixRoutesOnly - Associated L3 VNI and corresponding route targets only with
EVPN type-5 routes, not with EVPN type-2 routes.

Name       Vni    State  Svi          RouterMac          SystemMac          Vlan  NexthopCount  RouterMacCount  VXLANIntf  PrefixRoutesOnly
---------  -----  -----  -----------  -----------------  -----------------  ----  ------------  --------------  ---------  ----------------
SERVICE_A  10000  up     vlan1505_l3  48:b0:2d:0e:b7:9a  48:b0:2d:0e:b7:9a  1505  1             1               vxlan99    disabled      
```
```
cumulus@leaf1:mgmt:~$ nv show vrf SERVICE_A evpn bgp-info 
                       operational      
---------------------  -----------------
rd                     172.16.255.1:3   
local-vtep             172.16.255.1     
router-mac             48:b0:2d:0e:b7:9a
system-mac             48:b0:2d:0e:b7:9a
system-ip              172.16.255.1     
[import-route-target]  65001:10000      
[export-route-target]  65001:10000      
cumulus@leaf1:mgmt:~$
```

```
cumulus@leaf1:mgmt:~$ nv show evpn vni 10 bgp-info 
                           operational   
-------------------------  --------------
rd                         172.16.255.1:2
local-vtep                 172.16.255.1  
advertise-svi-ip           off           
advertise-default-gateway  off           
in-kernel                  on            
type                       L2            
mac-vrf-soo                              
[import-route-target]      65001:10      
[export-route-target]      65001:10      
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show vrf SERVICE_A evpn remote-router-mac 
MAC address        remote-vtep 
-----------------  ------------
48:b0:2d:aa:d4:e4  172.16.255.3
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show evpn vni 10 remote-vtep 

Flood - Remote-vtep flood type

RemoteVtep    Flood
------------  -----
172.16.255.2  HER  
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show evpn access-vlan-info
vlan
=======
    Id    MemberCnt  Vni  VniCnt  VxlanIntf  MemberIntf
    ----  ---------  ---  ------  ---------  ----------
    10               10   1       vxlan48              
    1505                  1       vxlan99              
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show interface vlan10 neighbor 
ipv4
=======
    IPV4        LLADR(MAC)       
    ----------  -----------------
    10.0.10.11  48:b0:2d:e4:a8:96
    10.0.10.22  48:b0:2d:2f:66:f5



ipv6
=======
    IPV6                       LLADR(MAC)       
    -------------------------  -----------------
    fe80::4ab0:2dff:fe2f:66f5  48:b0:2d:2f:66:f5
    fe80::4ab0:2dff:fee4:a896  48:b0:2d:e4:a8:96
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show vrf default router bgp address-family l2vpn-evpn route 

PathCnt - number of L2VPN EVPN per (RD, route-type) paths

Route                                                                     rd              route-type  PathCnt
------------------------------------------------------------------------  --------------  ----------  -------
[172.16.255.1:2]:[2]:[0]:[48:b0:2d:e4:a8:96]                              172.16.255.1:2  2           1      
[172.16.255.1:2]:[2]:[0]:[48:b0:2d:e4:a8:96]:[10.0.10.11]                 172.16.255.1:2  2           1      
[172.16.255.1:2]:[2]:[0]:[48:b0:2d:e4:a8:96]:[fe80::4ab0:2dff:fee4:a896]  172.16.255.1:2  2           1      
[172.16.255.1:2]:[3]:[0]:[172.16.255.1]                                   172.16.255.1:2  3           1      
[172.16.255.2:2]:[2]:[0]:[48:b0:2d:2f:66:f5]                              172.16.255.2:2  2           2      
[172.16.255.2:2]:[2]:[0]:[48:b0:2d:2f:66:f5]:[10.0.10.22]                 172.16.255.2:2  2           2      
[172.16.255.2:2]:[2]:[0]:[48:b0:2d:2f:66:f5]:[fe80::4ab0:2dff:fe2f:66f5]  172.16.255.2:2  2           2      
[172.16.255.2:2]:[3]:[0]:[172.16.255.2]                                   172.16.255.2:2  3           2      
[172.16.255.3:2]:[2]:[0]:[48:b0:2d:b1:fe:11]                              172.16.255.3:2  2           2      
[172.16.255.3:2]:[2]:[0]:[48:b0:2d:b1:fe:11]:[10.0.20.33]                 172.16.255.3:2  2           2      
[172.16.255.3:2]:[2]:[0]:[48:b0:2d:b1:fe:11]:[fe80::4ab0:2dff:feb1:fe11]  172.16.255.3:2  2           2      
[172.16.255.3:2]:[3]:[0]:[172.16.255.3]                                   172.16.255.3:2  3           2      
cumulus@leaf1:mgmt:~$                  
```
```
cumulus@leaf1:mgmt:~$ nv show evpn vni 10 host

LocMobSeq - local mobility sequence, RemMobSeq - remote mobility sequence, Esi -
Remote Esi

IP address                 Type    State   LocMobSeq  RemMobSeq  Mac                Esi
-------------------------  ------  ------  ---------  ---------  -----------------  ---
10.0.10.11                 local   active  0          0          48:b0:2d:e4:a8:96     
10.0.10.22                 remote  active  0          0          48:b0:2d:2f:66:f5     
fe80::4ab0:2dff:fe2f:66f5  remote  active  0          0          48:b0:2d:2f:66:f5     
fe80::4ab0:2dff:fee4:a896  local   active  0          0          48:b0:2d:e4:a8:96     
```
```
cumulus@leaf1:mgmt:~$ nv show evpn vni 10 mac

LocMobSeq - local mobility sequence, RemMobSeq - remote mobility sequence,
RemoteVtep - Remote Vtep address, Esi - Remote Esi

MAC address        Type    LocMobSeq  RemMobSeq  Interface  RemoteVtep    Esi
-----------------  ------  ---------  ---------  ---------  ------------  ---
48:b0:2d:2f:66:f5  remote  1          0                     172.16.255.2     
48:b0:2d:e4:a8:96  local   0          0          swp32                       
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show bridge domain br_l3vni vlan-vni-map 
vlan-vni-offset: -         
      VLAN        VNI         
      ----        -------     
      1505        10000       

cumulus@leaf1:mgmt:~$ nv show bridge domain br_l3vni vlan
Vlan  Ptp State  Source IP  VNI  
----  ---------  ---------  -----
1505                        10000
cumulus@leaf1:mgmt:~$ nv show bridge domain br_l3vni mac-table 
entry-id  MAC address        vlan  interface  remote-dst    src-vni  entry-type    last-update  age    
--------  -----------------  ----  ---------  ------------  -------  ------------  -----------  -------
1         48:b0:2d:74:2f:7c  1505  vxlan99                           extern_learn  0:14:24      0:14:24
2         48:b0:2d:aa:d4:e4  1505  vxlan99                           extern_learn  5:12:08      5:12:08
3         12:05:cf:b2:36:2f        vxlan99                           permanent     6:05:39      6:05:39
4         48:b0:2d:aa:d4:e4        vxlan99    172.16.255.3  10000    extern_learn  5:12:08      5:12:08
5         48:b0:2d:74:2f:7c        vxlan99    172.16.255.2  10000    extern_learn  0:14:24      0:14:24
6         48:b0:2d:0e:b7:9a  1505  br_l3vni                          permanent     6:05:39      6:05:39
7         48:b0:2d:0e:b7:9a  1     br_l3vni                          permanent     6:05:39      6:05:39
8         48:b0:2d:0e:b7:9a        br_l3vni                          permanent     6:05:39      6:05:39
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show bridge domain br_l3vni vlan
Vlan  Ptp State  Source IP  VNI  
----  ---------  ---------  -----
1505                        10000
cumulus@leaf1:mgmt:~$ nv show bridge domain br_l3vni vlan-vni-map 
vlan-vni-offset: -         
      VLAN        VNI         
      ----        -------     
      1505        10000       

cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show interface vxlan48
                           operational                   applied
-------------------------  ----------------------------  -------
type                       vxlan                                
vlan                       0                                    
bridge                                                          
  [domain]                 br_default                           
ptp                                                             
  state                    disabled                             
parent                     br_default                           
ipv4                                                            
  [address]                                                     
ipv6                                                            
  [address]                fe80::b013:71ff:fef2:e131/64         
link                                                            
  mac-address              b2:13:71:f2:e1:31                    
  mtu                      9216                                 
  [flag]                   broadcast                            
  [flag]                   multicast                            
  [flag]                   up                                   
  [flag]                   lower-up                             
  protodown                disabled                             
  oper-status              unknown                              
  admin-status             up                                   
  oper-status-last-change  Never                                
counters                                                        
  link                                                          
    carrier-transitions    0                                    
    carrier-up-count       0                                    
    carrier-down-count     0                                    
ifindex                    36
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show interface vxlan99
                           operational                   applied
-------------------------  ----------------------------  -------
type                       vxlan                                
vlan                       0                                    
bridge                                                          
  [domain]                 br_l3vni                             
ptp                                                             
  state                    disabled                             
parent                     br_l3vni                             
ipv4                                                            
  [address]                                                     
ipv6                                                            
  [address]                fe80::1005:cfff:feb2:362f/64         
link                                                            
  mac-address              12:05:cf:b2:36:2f                    
  mtu                      9216                                 
  [flag]                   broadcast                            
  [flag]                   multicast                            
  [flag]                   up                                   
  [flag]                   lower-up                             
  protodown                disabled                             
  oper-status              unknown                              
  admin-status             up                                   
  oper-status-last-change  Never                                
counters                                                        
  link                                                          
    carrier-transitions    0                                    
    carrier-up-count       0                                    
    carrier-down-count     0                                    
ifindex                    40                                   
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show interface vlan1505_l3 
                           operational                   applied
-------------------------  ----------------------------  -------
type                       svi                                  
base-interface             br_l3vni                             
vrf                        SERVICE_A                            
vlan                       1505                                 
ptp                                                             
  state                    disabled                             
parent                     SERVICE_A                            
ipv4                                                            
  [address]                                                     
ipv6                                                            
  [address]                fe80::4ab0:2dff:fe0e:b79a/64         
link                                                            
  mac-address              48:b0:2d:0e:b7:9a                    
  mtu                      9216                                 
  [flag]                   broadcast                            
  [flag]                   multicast                            
  [flag]                   up                                   
  [flag]                   lower-up                             
  protodown                disabled                             
  oper-status              up                                   
  admin-status             up                                   
  oper-status-last-change  2026/04/15 11:05:10.230              
counters                                                        
  link                                                          
    carrier-transitions    1                                    
    carrier-up-count       1                                    
    carrier-down-count     0                                    
ifindex                    42                                   
cumulus@leaf1:mgmt:~$
```
