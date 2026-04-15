
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
