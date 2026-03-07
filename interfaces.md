- To view the status of links/interfaces, run `nv show interface` or `nv show interface brief`. The columns `Remote Host` and `Remote Port` show the brief information of connected hosts or connected devices:

  ```
  cumulus@Leaf-1.netlabbuilder.net:~$ nv show interface
  Interface  Admin Status  Oper Status  Speed  MTU    Type      Remote Host  Remote Port        Summary                                   
  ---------  ------------  -----------  -----  -----  --------  -----------  -----------------  ------------------------------------------
  eth0       up            up           1G     1500   eth                                       IPv6 Address: fe80::4ab0:2dff:fed5:f151/64
  lo         up            unknown             65536  loopback                                  IPv4 Address:                  127.0.0.1/8
                                                                                                Address type:                      primary
                                                                                                IPv6 Address:                      ::1/128
  mgmt       up            up                  65575  vrf                                       IPv4 Address:                  127.0.0.1/8
                                                                                                IPv4 Address:                  127.0.1.1/8
                                                                                                Address type:                      primary
                                                                                                Address type:                    secondary
                                                                                                IPv6 Address:                      ::1/128
  swp1       up            up                  1500   swp       cumulus      swp1               IPv6 Address: fe80::4ab0:2dff:fe07:6854/64
  swp2       up            up                  1500   swp       cumulus      swp1               IPv6 Address: fe80::4ab0:2dff:fe4a:6825/64
  swp3       up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:feb5:7ec1/64
  swp4       up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe5e:a914/64
  swp5       up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe4b:e6e0/64
  swp6       up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fef6:ed6a/64
  swp7       up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe86:b71c/64
  swp8       up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe51:1dc3/64
  swp9       up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe2e:39ee/64
  swp10      up            up                  1500   swp                                       IPv6 Address:  fe80::4ab0:2dff:feb1:694/64
  swp11      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fedf:a96f/64
  swp12      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe40:6cb0/64
  swp13      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe96:95e3/64
  swp14      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe82:c60c/64
  swp15      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe34:48bb/64
  swp16      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe57:6b0d/64
  swp17      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe66:9aab/64
  swp18      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fee7:1bd7/64
  swp19      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fee3:8e49/64
  swp20      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fed2:b8f5/64
  swp21      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fef1:7b42/64
  swp22      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe73:3724/64
  swp23      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe4c:2113/64
  swp24      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe5b:eba2/64
  swp25      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:feb1:46a9/64
  swp26      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe33:f3d0/64
  swp27      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe20:28b6/64
  swp28      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe92:3245/64
  swp29      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe96:af7c/64
  swp30      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fec2:56c4/64
  swp31      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fefc:b3a4/64
  swp32      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fedc:71bc/64
  swp33      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:feda:a7a3/64
  swp34      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fecf:abb3/64
  swp35      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe0a:ca78/64
  swp36      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe24:5e92/64
  swp37      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:feeb:2dc5/64
  swp38      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe09:52e7/64
  swp39      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe61:e836/64
  swp40      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe3b:d361/64
  swp41      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe85:fbe8/64
  swp42      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe64:5d2a/64
  swp43      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe9c:acde/64
  swp44      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe67:1f72/64
  swp45      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fefd:f1f5/64
  swp46      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe2e:86a8/64
  swp47      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fed5:ebcd/64
  swp48      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe0e:b73c/64
  swp49      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fed8:9aa5/64
  swp50      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:feea:a827/64
  swp51      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe4d:b72f/64
  swp52      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:feea:282c/64
  swp53      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe72:a406/64
  swp54      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fec8:9ebc/64
  swp55      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe35:676b/64
  swp56      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fec6:e387/64
  swp57      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fefb:f984/64
  swp58      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe95:3e08/64
  swp59      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe18:268d/64
  swp60      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:feaa:999d/64
  swp61      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fe99:12de/64
  swp62      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fed3:2320/64
  swp63      up            up                  1500   swp                                       IPv6 Address: fe80::4ab0:2dff:fef9:b81c/64
  swp64      up            up                  1500   swp                                       IPv6 Address:  fe80::4ab0:2dff:fe58:af4/64
  swp65      up            up                  1500   swp       ubuntu       48:b0:2d:27:5f:50  IPv6 Address:  fe80::4ab0:2dff:fe9d:4d4/64
  cumulus@Leaf-1.netlabbuilder.net:~$ 
  ```
- To view `up` or `down` links/interfaces, run `nv show interface up` or `nv show interface down`:
  ```
  cumulus@Leaf-1.netlabbuilder.net:~$ nv show interface down
  Interface  Admin Status  Oper Status  Speed  MTU    Type      Summary                  
  ---------  ------------  -----------  -----  -----  --------  -------------------------
  lo         up            unknown             65536  loopback  IPv4 Address: 127.0.0.1/8
                                                                Address type:     primary
                                                                IPv6 Address:     ::1/128
  cumulus@Leaf-1.netlabbuilder.net:~$ nv show interface up
  Interface  Admin Status  Oper Status  Speed  MTU    Type  Remote Host  Remote Port        Summary                                   
  ---------  ------------  -----------  -----  -----  ----  -----------  -----------------  ------------------------------------------
  eth0       up            up           1G     1500   eth                                   IPv6 Address: fe80::4ab0:2dff:fed5:f151/64
  mgmt       up            up                  65575  vrf                                   IPv4 Address:                  127.0.0.1/8
                                                                                            IPv4 Address:                  127.0.1.1/8
                                                                                            Address type:                      primary
                                                                                            Address type:                    secondary
                                                                                            IPv6 Address:                      ::1/128
  swp1       up            up                  1500   swp   cumulus      swp1               IPv6 Address: fe80::4ab0:2dff:fe07:6854/64
  swp2       up            up                  1500   swp   cumulus      swp1               IPv6 Address: fe80::4ab0:2dff:fe4a:6825/64
  swp3       up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:feb5:7ec1/64
  swp4       up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe5e:a914/64
  swp5       up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe4b:e6e0/64
  swp6       up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fef6:ed6a/64
  swp7       up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe86:b71c/64
  swp8       up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe51:1dc3/64
  swp9       up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe2e:39ee/64
  swp10      up            up                  1500   swp                                   IPv6 Address:  fe80::4ab0:2dff:feb1:694/64
  swp11      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fedf:a96f/64
  swp12      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe40:6cb0/64
  swp13      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe96:95e3/64
  swp14      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe82:c60c/64
  swp15      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe34:48bb/64
  swp16      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe57:6b0d/64
  swp17      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe66:9aab/64
  swp18      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fee7:1bd7/64
  swp19      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fee3:8e49/64
  swp20      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fed2:b8f5/64
  swp21      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fef1:7b42/64
  swp22      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe73:3724/64
  swp23      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe4c:2113/64
  swp24      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe5b:eba2/64
  swp25      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:feb1:46a9/64
  swp26      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe33:f3d0/64
  swp27      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe20:28b6/64
  swp28      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe92:3245/64
  swp29      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe96:af7c/64
  swp30      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fec2:56c4/64
  swp31      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fefc:b3a4/64
  swp32      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fedc:71bc/64
  swp33      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:feda:a7a3/64
  swp34      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fecf:abb3/64
  swp35      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe0a:ca78/64
  swp36      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe24:5e92/64
  swp37      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:feeb:2dc5/64
  swp38      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe09:52e7/64
  swp39      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe61:e836/64
  swp40      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe3b:d361/64
  swp41      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe85:fbe8/64
  swp42      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe64:5d2a/64
  swp43      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe9c:acde/64
  swp44      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe67:1f72/64
  swp45      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fefd:f1f5/64
  swp46      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe2e:86a8/64
  swp47      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fed5:ebcd/64
  swp48      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe0e:b73c/64
  swp49      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fed8:9aa5/64
  swp50      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:feea:a827/64
  swp51      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe4d:b72f/64
  swp52      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:feea:282c/64
  swp53      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe72:a406/64
  swp54      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fec8:9ebc/64
  swp55      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe35:676b/64
  swp56      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fec6:e387/64
  swp57      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fefb:f984/64
  swp58      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe95:3e08/64
  swp59      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe18:268d/64
  swp60      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:feaa:999d/64
  swp61      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fe99:12de/64
  swp62      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fed3:2320/64
  swp63      up            up                  1500   swp                                   IPv6 Address: fe80::4ab0:2dff:fef9:b81c/64
  swp64      up            up                  1500   swp                                   IPv6 Address:  fe80::4ab0:2dff:fe58:af4/64
  swp65      up            up                  1500   swp   ubuntu       48:b0:2d:27:5f:50  IPv6 Address:  fe80::4ab0:2dff:fe9d:4d4/64
  cumulus@Leaf-1.netlabbuilder.net:~$
  ```
- To view the lldp information of connected hosts or connected devices, run `nv show interface lldp` or `nv show interface lldp-detail`:
  ```
  cumulus@Leaf-1.netlabbuilder.net:~$ nv show interface lldp
  Interface  Speed  Type  Remote Host  Remote Port      
  ---------  -----  ----  -----------  -----------------
  swp1              swp   cumulus      swp1             
  swp2              swp   cumulus      swp1             
  swp65             swp   ubuntu       48:b0:2d:27:5f:50
  cumulus@Leaf-1.netlabbuilder.net:~$ 
  cumulus@Leaf-1.netlabbuilder.net:~$ nv show interface lldp-detail 
  -------------------------------------------------------------------------------
  LLDP neighbors:
  -------------------------------------------------------------------------------
  
  Interface:    swp1
  -------------------------------------------------------------------------------
    Time:  
      0 days, 02:58:28
  
    Chassis:
      ChassisID:    mac 48:b0:2d:ec:e5:3b
      SysName:      cumulus
      SysDescr:     Cumulus Linux version 5.16.0 running on QEMU Standard PC (i440FX + PIIX, 1996)
      MgmtIP:       fe80::4ab0:2dff:feec:e53b
      MgmtIface:    2
      MgmtIP:       127.0.1.1
      MgmtIface:    68
      Capability:   Bridge, off
      Capability:   Router, on
    Port:
      PortID:       ifname swp1
      PortDescr:    swp1
      TTL:          120
      MFS:          1500
      PMD autoneg: supported: no, enabled: no
    LLDP-MED:
      Device Type:  Network Connectivity Device
      Capability:   Capabilities, yes
      Capability:   Inventory, yes
      Capability:   Location, yes
      Capability:   MDI/PD, yes
      Capability:   MDI/PSE, yes
      Capability:   Policy, yes
  
  Interface:    swp2
  -------------------------------------------------------------------------------
    Time:  
      0 days, 02:58:26
  
    Chassis:
      ChassisID:    mac 48:b0:2d:e8:28:a4
      SysName:      cumulus
      SysDescr:     Cumulus Linux version 5.16.0 running on QEMU Standard PC (i440FX + PIIX, 1996)
      MgmtIP:       fe80::4ab0:2dff:fee8:28a4
      MgmtIface:    2
      MgmtIP:       127.0.1.1
      MgmtIface:    68
      Capability:   Bridge, off
      Capability:   Router, on
    Port:
      PortID:       ifname swp1
      PortDescr:    swp1
      TTL:          120
      MFS:          1500
      PMD autoneg: supported: no, enabled: no
    LLDP-MED:
      Device Type:  Network Connectivity Device
      Capability:   Capabilities, yes
      Capability:   Inventory, yes
      Capability:   Location, yes
      Capability:   MDI/PD, yes
      Capability:   MDI/PSE, yes
      Capability:   Policy, yes
  
  Interface:    swp65
  -------------------------------------------------------------------------------
    Time:  
      0 days, 02:58:26
  
    Chassis:
      ChassisID:    mac 48:b0:2d:27:5f:50
      SysName:      ubuntu
      SysDescr:     Ubuntu 24.04.1 LTS Linux 6.8.0-48-generic #48-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 14:04:52 UTC 2024 x86_64
      MgmtIP:       fe80::4ab0:2dff:fe27:5f50
      MgmtIface:    2
      Capability:   Bridge, off
      Capability:   Router, off
    Port:
      PortID:       ifname 48:b0:2d:27:5f:50
      PortDescr:    eth0
      TTL:          120
      MFS:          -
      PMD autoneg: supported: yes, enabled: yes
        Adv:          10Base-T, HD: yes, FD: yes
        Adv:          100Base-TX, HD: yes, FD: yes
        Adv:          1000Base-T, HD: no, FD: yes
        MAU oper type: 1000BaseTFD - Four-pair Category 5 UTP, full duplex mode
    LLDP-MED:
      Device Type:  
  -------------------------------------------------------------------------------
  
  cumulus@Leaf-1.netlabbuilder.net:~$
  ```
