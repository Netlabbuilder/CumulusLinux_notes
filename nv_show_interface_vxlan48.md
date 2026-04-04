- To view all interfaces, run `nv show interface`:

  The interface `vxlan48` has operational status (`Oper Status`) of `unknown`, while its admin status (`Admin Status`) is `up`
  ```
  cumulus@leaf1:mgmt:~$ nv show interface
  Interface   Admin Status  Oper Status  Speed  MTU    Type      Remote Host  Remote Port  Summary                                   
  ----------  ------------  -----------  -----  -----  --------  -----------  -----------  ------------------------------------------
  br_default  up            up                  9216   bridge                              IPv6 Address: fe80::4ab0:2dff:fe7e:3e38/64
  eth0        up            up           1G     1500   eth                                 IPv6 Address: fe80::4ab0:2dff:fe7e:3e17/64
  lo          up            unknown             65536  loopback                            IPv4 Address:                  127.0.0.1/8
                                                                                           IPv4 Address:              172.16.255.1/32
                                                                                           Address type:                      primary
                                                                                           Address type:                      primary
                                                                                           IPv6 Address:                      ::1/128
  mgmt        up            up                  65575  vrf                                 IPv4 Address:                  127.0.0.1/8
                                                                                           IPv4 Address:                  127.0.1.1/8
                                                                                           Address type:                      primary
                                                                                           Address type:                    secondary
                                                                                           IPv6 Address:                      ::1/128
  swp1        up            up           1G     9216   swp       spine1       swp1         IPv4 Address:                172.16.1.1/31
                                                                                           Address type:                      primary
                                                                                           IPv6 Address: fe80::4ab0:2dff:fea6:9191/64
  swp2        up            up           1G     9216   swp       spine2       swp1         IPv4 Address:                172.16.2.1/31
                                                                                           Address type:                      primary
                                                                                           IPv6 Address: fe80::4ab0:2dff:fefe:a553/64
  swp3        down          down                1500   swp                                                                           
  swp4        down          down                1500   swp                                                                           
  swp5        down          down                1500   swp                                                                           
  swp6        down          down                1500   swp                                                                           
  swp7        down          down                1500   swp                                                                           
  swp8        down          down                1500   swp                                                                           
  swp9        down          down                1500   swp                                                                           
  swp10       down          down                1500   swp                                                                           
  swp11       down          down                1500   swp                                                                           
  swp12       down          down                1500   swp                                                                           
  swp13       down          down                1500   swp                                                                           
  swp14       down          down                1500   swp                                                                           
  swp15       down          down                1500   swp                                                                           
  swp16       down          down                1500   swp                                                                           
  swp17       down          down                1500   swp                                                                           
  swp18       down          down                1500   swp                                                                           
  swp19       down          down                1500   swp                                                                           
  swp20       down          down                1500   swp                                                                           
  swp21       down          down                1500   swp                                                                           
  swp22       down          down                1500   swp                                                                           
  swp23       down          down                1500   swp                                                                           
  swp24       down          down                1500   swp                                                                           
  swp25       down          down                1500   swp                                                                           
  swp26       down          down                1500   swp                                                                           
  swp27       down          down                1500   swp                                                                           
  swp28       down          down                1500   swp                                                                           
  swp29       down          down                1500   swp                                                                           
  swp30       down          down                1500   swp                                                                           
  swp31       down          down                1500   swp                                                                           
  swp32       up            up           1G     9216   swp                                                                           
  vxlan48     up            unknown             9216   vxlan                               IPv6 Address: fe80::e48b:2aff:fe20:a299/64
  cumulus@leaf1:mgmt:~$
  ```
- To view details of the interface `vxlan48`:

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
      [address]                fe80::e48b:2aff:fe20:a299/64         
    link                                                            
      mac-address              e6:8b:2a:20:a2:99                    
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
