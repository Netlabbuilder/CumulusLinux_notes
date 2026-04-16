
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
```
cumulus@leaf1:mgmt:~$ nv show vrf SERVICE_A router bgp route-export 
                  operational  applied
----------------  -----------  -------
to-evpn                               
  [route-target]               auto   
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf1:mgmt:~$ nv show vrf SERVICE_A router bgp route-import 
                  operational  applied
----------------  -----------  -------
from-evpn                             
  [route-target]               auto   
cumulus@leaf1:mgmt:~$
```
```
cumulus@leaf01:mgmt:~$ sudo vtysh
leaf1# show bgp l2vpn evpn
BGP table version is 4, local router ID is 172.16.255.1
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal
Origin codes: i - IGP, e - EGP, ? - incomplete
EVPN type-1 prefix: [1]:[EthTag]:[ESI]:[IPlen]:[VTEP-IP]:[Frag-id]
EVPN type-2 prefix: [2]:[EthTag]:[MAClen]:[MAC]:[IPlen]:[IP]
EVPN type-3 prefix: [3]:[EthTag]:[IPlen]:[OrigIP]
EVPN type-4 prefix: [4]:[ESI]:[IPlen]:[OrigIP]
EVPN type-5 prefix: [5]:[EthTag]:[IPlen]:[IP]

   Network          Next Hop            Metric LocPrf Weight Path
Route Distinguisher: 172.16.255.1:2
 *> [2]:[0]:[48]:[48:b0:2d:e4:a8:96]
                    172.16.255.1 (leaf1)
                                                       32768 i
                    ET:8 RT:65001:10
 *> [2]:[0]:[48]:[48:b0:2d:e4:a8:96]:[32]:[10.0.10.11]
                    172.16.255.1 (leaf1)
                                                       32768 i
                    ET:8 RT:65001:10 RT:65001:10000 Rmac:48:b0:2d:0e:b7:9a
 *> [2]:[0]:[48]:[48:b0:2d:e4:a8:96]:[128]:[fe80::4ab0:2dff:fee4:a896]
                    172.16.255.1 (leaf1)
                                                       32768 i
                    ET:8 RT:65001:10
 *> [3]:[0]:[32]:[172.16.255.1]
                    172.16.255.1 (leaf1)
                                                       32768 i
                    ET:8 RT:65001:10
Route Distinguisher: 172.16.255.2:2
 *> [2]:[0]:[48]:[48:b0:2d:2f:66:f5]
                    172.16.255.2 (spine2)
                                                           0 65999 65002 i
                    RT:65002:10 ET:8
 *                   172.16.255.2 (spine1)
                                                           0 65999 65002 i
                    RT:65002:10 ET:8
 *> [2]:[0]:[48]:[48:b0:2d:2f:66:f5]:[32]:[10.0.10.22]
                    172.16.255.2 (spine1)
                                                           0 65999 65002 i
                    RT:65002:10 RT:65002:10000 ET:8 Rmac:48:b0:2d:74:2f:7c
 *                   172.16.255.2 (spine2)
                                                           0 65999 65002 i
                    RT:65002:10 RT:65002:10000 ET:8 Rmac:48:b0:2d:74:2f:7c
 *> [2]:[0]:[48]:[48:b0:2d:2f:66:f5]:[128]:[fe80::4ab0:2dff:fe2f:66f5]
                    172.16.255.2 (spine1)
                                                           0 65999 65002 i
                    RT:65002:10 ET:8
 *                   172.16.255.2 (spine2)
                                                           0 65999 65002 i
                    RT:65002:10 ET:8
 *> [3]:[0]:[32]:[172.16.255.2]
                    172.16.255.2 (spine2)
                                                           0 65999 65002 i
                    RT:65002:10 ET:8
 *                   172.16.255.2 (spine1)
                                                           0 65999 65002 i
                    RT:65002:10 ET:8
Route Distinguisher: 172.16.255.3:2
 *> [2]:[0]:[48]:[48:b0:2d:b1:fe:11]
                    172.16.255.3 (spine1)
                                                           0 65999 65003 i
                    RT:65003:20 ET:8
 *                   172.16.255.3 (spine2)
                                                           0 65999 65003 i
                    RT:65003:20 ET:8
 *> [2]:[0]:[48]:[48:b0:2d:b1:fe:11]:[32]:[10.0.20.33]
                    172.16.255.3 (spine1)
                                                           0 65999 65003 i
                    RT:65003:20 RT:65003:10000 ET:8 Rmac:48:b0:2d:aa:d4:e4
 *                   172.16.255.3 (spine2)
                                                           0 65999 65003 i
                    RT:65003:20 RT:65003:10000 ET:8 Rmac:48:b0:2d:aa:d4:e4
 *> [2]:[0]:[48]:[48:b0:2d:b1:fe:11]:[128]:[fe80::4ab0:2dff:feb1:fe11]
                    172.16.255.3 (spine1)
                                                           0 65999 65003 i
                    RT:65003:20 ET:8
 *                   172.16.255.3 (spine2)
                                                           0 65999 65003 i
                    RT:65003:20 ET:8
 *> [3]:[0]:[32]:[172.16.255.3]
                    172.16.255.3 (spine1)
                                                           0 65999 65003 i
                    RT:65003:20 ET:8
 *                   172.16.255.3 (spine2)
                                                           0 65999 65003 i
                    RT:65003:20 ET:8

Displayed 12 out of 20 total prefixes
leaf1#
```
```
leaf1# show bgp l2vpn evpn summary 
BGP router identifier 172.16.255.1, local AS number 65001 VRF default vrf-id 0
BGP table version 0
RIB entries 5, using 640 bytes of memory
Peers 2, using 44 KiB of memory
Peer groups 3, using 192 bytes of memory

Neighbor               V         AS   MsgRcvd   MsgSent   TblVer  InQ OutQ  Up/Down State/PfxRcd   PfxSnt Desc
spine1(172.16.255.253) 4      65999      9821      9821        4    0    0 08:10:03            8       12 EBGP_OVERLAY_SPINES
spine2(172.16.255.254) 4      65999      9821      9821        4    0    0 08:10:04            8       12 EBGP_OVERLAY_SPINES

Total number of neighbors 2
leaf1#
```
```
leaf1# show bgp l2vpn evpn vni 
Advertise Gateway Macip: Disabled
Advertise SVI Macip: Disabled
Advertise All VNI flag: Enabled
BUM flooding: Head-end replication
VXLAN flooding: Enabled
Number of L2 VNIs: 1
Number of L3 VNIs: 1
Flags: * - Kernel
  VNI        Type RD                    Import RT                 Export RT                 MAC-VRF Site-of-Origin    Tenant VRF                           
* 10         L2   172.16.255.1:2        65001:10                  65001:10                                            SERVICE_A                            
* 10000      L3   172.16.255.1:3        65001:10000               65001:10000                                         SERVICE_A                            
leaf1#
```
```
leaf1# show bgp l2vpn evpn vni 10
VNI: 10 (known to the kernel)
  Type: L2
  Tenant-Vrf: SERVICE_A
  RD: 172.16.255.1:2
  Originator IP: 172.16.255.1
  Mcast group: 0.0.0.0
  MAC-VRF Site-of-Origin: 
  Advertise-gw-macip : Disabled
  Advertise-svi-macip : Disabled
  SVI interface : vlan10
  Import Route Target:
    65001:10
  Export Route Target:
    65001:10
leaf1#
```
```
leaf1# show bgp l2vpn evpn vni 10000
VNI: 10000 (known to the kernel)
  Type: L3
  Tenant VRF: SERVICE_A
  RD: 172.16.255.1:3
  Originator IP: 172.16.255.1
  MAC-VRF Site-of-Origin: 
  Advertise-gw-macip : n/a
  Advertise-svi-macip : n/a
  Advertise-pip: Yes
  System-IP: 172.16.255.1
  System-MAC: 48:b0:2d:0e:b7:9a
  Router-MAC: 48:b0:2d:0e:b7:9a
  Import Route Target:
    65001:10000
  Export Route Target:
    65001:10000
leaf1#
```
