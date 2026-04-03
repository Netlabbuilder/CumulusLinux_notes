### Reference Resources:

- [NVUE Command Reference](https://docs.nvidia.com/networking-ethernet-software/nvue-reference/Show-Commands/BGP/)

### Examples:

- To view global BGP configuration, run `nv show router bgp`:

  ```
  cumulus@spine1:mgmt:~$ nv show router bgp
                                  operational     applied       
  ------------------------------  --------------  --------------
  state                           enabled         enabled       
  autonomous-system               65253           65253         
  router-id                       172.16.255.253  172.16.255.253
  policy-update-timer             5               5             
  graceful-shutdown               disabled        disabled      
  wait-for-install                disabled        disabled      
  graceful-restart                                              
    mode                          helper-only     helper-only   
    restart-time                  120             120           
    path-selection-deferral-time  120             120           
    stale-routes-time             360             360           
  convergence-wait                                              
    time                          0               0             
    establish-wait-time           0               0             
  queue-limit                                                   
    input                         10000           10000         
    output                        10000           10000         
  cumulus@spine1:mgmt:~$
  ```
- To view a summary of the BGP configuration information for the specified VRF, run `nv show vrf <vrf-id> router bgp`:
  ```
  cumulus@spine1:mgmt:~$ nv show vrf default router bgp
                                     operational     applied   
  ---------------------------------  --------------  ----------
  state                                              enabled   
  autonomous-system                  65253           auto      
  router-id                          172.16.255.253  auto      
  rd                                                 none      
  soo-source                                         none      
  address-family                                               
    ipv4-unicast                                               
      rib-filter                                     none      
      route-export                                             
        to-evpn                                                
          state                                      disabled  
          default-route-origination  disabled                  
        to-vrf                                                 
          [list]                     none                      
        [route-target]               none                      
        rd                           none                      
      route-import                                             
        from-vrf                                               
          state                                      disabled  
          [list]                     none                      
        [route-target]               none                      
      admin-distance                                           
        external                     20              20        
        internal                     200             200       
      multipaths                                               
        ebgp                         64              64        
        ibgp                         64              64        
        compare-cluster-length       disabled        disabled  
      state                                          enabled   
      redistribute                                             
        static                                                 
          state                      disabled        disabled  
        connected                                              
          state                      disabled        disabled  
        kernel                                                 
          state                      disabled        disabled  
        ospf                                                   
          state                      disabled        disabled  
      [network]                                                
      [aggregate-route]                                        
    ipv6-unicast                                               
      route-export                                             
        to-evpn                                                
          default-route-origination  disabled                  
        to-vrf                                                 
          [list]                     none                      
        [route-target]               none                      
        rd                           none                      
      route-import                                             
        from-vrf                                               
          [list]                     none                      
        [route-target]               none                      
      multipaths                                               
        compare-cluster-length       disabled                  
      state                                          disabled  
      redistribute                                             
        static                                                 
          state                      disabled                  
        connected                                              
          state                      disabled                  
        kernel                                                 
          state                      disabled                  
        ospf6                                                  
          state                      disabled                  
    l2vpn-evpn                                                 
      state                                          disabled  
    ipv4-unreachability                                        
      state                                          disabled  
    ipv6-unreachability                                        
      state                                          disabled  
  [neighbor]                         172.16.1.1      172.16.1.1
  [neighbor]                         172.16.1.3      172.16.1.3
  [neighbor]                         172.16.1.5      172.16.1.5
  [neighbor]                         172.16.1.7      172.16.1.7
  [peer-group]                                                 
  path-selection                                               
    routerid-compare                 disabled        disabled  
    use-imported-attributes          disabled        disabled  
    aspath                                                     
      compare-lengths                enabled         enabled   
      compare-confed                 disabled        disabled  
    med                                                        
      compare-always                 disabled        disabled  
      compare-deterministic          enabled         enabled   
      compare-confed                 disabled        disabled  
      missing-as-max                 disabled        disabled  
    multipath                                                  
      aspath-ignore                  disabled        disabled  
      generate-asset                 disabled        disabled  
      bandwidth                      all-paths       all-paths 
  route-reflection                                             
    state                                            disabled  
    reflect-between-clients          enabled                   
    outbound-policy                  disabled                  
  route-export                                                 
    to-evpn                                                    
      [route-target]                                 auto      
  route-import                                                 
    from-evpn                                                  
      [route-target]                                 auto      
  timers                                                       
    keepalive                                        3         
    hold                                             9         
    connection-retry                 10              10        
    route-advertisement              none            none      
    conditional-advertise                            60        
  confederation                                                
    id                                               none      
    [member-as]                                                
  dynamic-neighbor                                             
    [listen-range]                                             
    limit                                            100       
  configured-neighbors               4                         
  established-neighbors              4                         
  cumulus@spine1:mgmt:~$
  ```
- To view information about all BGP neighbors, run `nv show vrf <vrf-id> router bgp neighbor`:

  ```
  cumulus@spine1:mgmt:~$ nv show vrf default router bgp neighbor 

  Hostname - Hostname, AS - Remote Autonomous System, Uptime - BGP session up
  time, ResetTime - Last connection reset time, Afi-Safi - Address family, PfxSent
  - Transmitted prefix counter, PfxRcvd - Recieved prefix counter
  
  Neighbor    Hostname  AS     State        Uptime   ResetTime  MsgRcvd  MsgSent  Afi-Safi      PfxSent  PfxRcvd
  ----------  --------  -----  -----------  -------  ---------  -------  -------  ------------  -------  -------
  172.16.1.1  leaf1     65001  established  1:12:43  1:12:44    1457     1457     ipv4-unicast  0        0      
  172.16.1.3  leaf2     65002  established  1:12:43  1:12:44    1457     1457     ipv4-unicast  0        0      
  172.16.1.5  leaf3     65003  established  1:12:43  1:12:44    1457     1457     ipv4-unicast  0        0      
  172.16.1.7  leaf4     65004  established  1:12:43  1:12:44    1457     1457     ipv4-unicast  0        0      
  cumulus@spine1:mgmt:~$
  ```
- To view global configuration and statistics for the specified BGP neighbor, run `nv show vrf <vrf-id> router bgp neighbor <neighbor-id>`:

  ```
  cumulus@spine1:mgmt:~$ nv show vrf default router bgp neighbor 172.16.1.1
                                      operational                applied                                
  ----------------------------------  -------------------------  ---------------------------------------
  password                                                       $nvsec$d1a028e8c7f97db92876c2a30fcc403f
  enforce-first-as                                               enabled                                
  passive-mode                                                   disabled                               
  nexthop-connected-check                                        enabled                                
  description                                                    none                                   
  graceful-shutdown                                              disabled                               
  ttl-security                                                                                          
    state                             enabled                    disabled                               
    hops                              1                                                                 
  local-as                                                                                              
    state                                                        disabled                               
    asn                               65253                                                             
    prepend                           enabled                                                           
    replace                           disabled                                                          
  timers                                                                                                
    keepalive                         3                          auto                                   
    hold                              9                          auto                                   
    connection-retry                  10                         auto                                   
    route-advertisement               none                       auto                                   
  address-family                                                                                        
    ipv4-unicast                                                                                        
      state                                                      enabled                                
      route-reflector-client                                     disabled                               
      soft-reconfiguration                                       disabled                               
      nexthop-setting                                            auto                                   
      add-path-tx                                                off                                    
      attribute-mod                                                                                     
        aspath                        disabled                   disabled                               
        med                           disabled                   disabled                               
        nexthop                       disabled                   disabled                               
      aspath                                                                                            
        replace-peer-as               disabled                   disabled                               
        private-as                    none                       none                                   
        allow-my-asn                                                                                    
          state                       disabled                   disabled                               
      update-group                    1                                                                 
      tx-prefix                       0                                                                 
      rx-prefix                       0                                                                 
      capabilities                                                                                      
        rx-addpath                    on                                                                
        tx-addpath                    off                                                               
        rx-mpbgp                      on                                                                
        tx-mpbgp                      on                                                                
        rx-graceful-restart           on                                                                
        rx-restart-f-bit              off                                                               
      graceful-restart                                                                                  
        rx-eof-rib                    on                                                                
        tx-eof-rib                    on                                                                
        tx-eof-rib-sent-after-update  on                                                                
        timers                                                                                          
          stale-path                                                                                    
            timer-sec                 360                                                               
      weight                                                     0                                      
      community-advertise                                                                               
        regular                       enabled                    enabled                                
        extended                      enabled                    enabled                                
        large                         enabled                    enabled                                
      conditional-advertise                                                                             
        state                                                    disabled                               
      policy                                                                                            
        inbound                                                                                         
          route-map                                              none                                   
          prefix-list                                            none                                   
          aspath-list                                            none                                   
        outbound                                                                                        
          route-map                                              none                                   
          unsuppress-map                                         none                                   
          prefix-list                                            none                                   
          aspath-list                                            none                                   
      default-route-origination                                                                         
        state                                                    disabled                               
      prefix-limits                                                                                     
        inbound                                                                                         
          maximum                                                none                                   
          warning-threshold                                      75                                     
          warning-only                disabled                                                          
    ipv6-unicast                                                                                        
      state                                                      disabled                               
    l2vpn-evpn                                                                                          
      state                                                      disabled                               
    ipv4-unreachability                                                                                 
      state                                                      disabled                               
    ipv6-unreachability                                                                                 
      state                                                      disabled                               
  state                                                          enabled                                
  type                                                           numbered                               
  peer-group                                                     none                                   
  remote-as                           65001                      external                               
  capabilities                                                                                          
    extended-nexthop                                             auto                                   
    tx-asn32                          on                                                                
    rx-asn32                          off                                                               
    tx-route-refresh                  on                                                                
    rx-route-refresh                  on                                                                
    tx-graceful-restart               on                                                                
    rx-graceful-restart               on                                                                
    rx-restart-r-bit                  off                                                               
  graceful-restart                                                                                      
    remote-mode                       helper-only                                                       
    rx-restart-time                   120                                                               
    mode                              auto                       auto                                   
  local-hostname                      spine1                                                            
  local-domain                        n/a                                                               
  remote-hostname                     leaf1                                                             
  remote-domain                       n/a                                                               
  bgp-version                         4                                                                 
  remote-router-id                    172.16.255.1                                                      
  session-state                       established                                                       
  uptime                              1:14:03                                                           
  connection-type                     shared-network                                                    
  connections-established             1                                                                 
  connections-dropped                 0                                                                 
  last-reset-time                     1:14:04                                                           
  last-reset-reason                   Waiting for peer OPEN                                             
  last-reset-code                     32                                                                
  local-ip                            172.16.1.0                                                        
  remote-ip                           172.16.1.1                                                        
  local-port                          54668                                                             
  remote-port                         179                                                               
  nexthop                                                                                               
    ipv4                              172.16.1.0                                                        
    ipv6-global                       fe80::4ab0:2dff:feea:60e4                                         
    ipv6-local                        fe80::4ab0:2dff:feea:60e4                                         
  message-stats                                                                                         
    input-queue                       0                                                                 
    output-queue                      0                                                                 
    rx-opens                          1                                                                 
    tx-opens                          1                                                                 
    rx-keepalives                     1482                                                              
    tx-keepalives                     1481                                                              
    rx-route-refreshes                0                                                                 
    tx-route-refreshes                0                                                                 
    tx-total                          1483                                                              
    rx-total                          1484                                                              
  cumulus@spine1:mgmt:~$
  ```
