```
cumulus@leaf2:mgmt:~$ nv config show -o commands
nv set bridge domain br_default type vlan-aware
nv set bridge domain br_default vlan 10 vni 10
nv set evpn state enabled
nv set interface eth0 ipv4 dhcp-client set-hostname enabled
nv set interface eth0 ipv4 dhcp-client state enabled
nv set interface eth0 type eth
nv set interface eth0 vrf mgmt
nv set interface lo ipv4 address 172.16.255.2/32
nv set interface lo type loopback
nv set interface swp1 ipv4 address 172.16.1.3/31
nv set interface swp1-2,32 type swp
nv set interface swp2 ipv4 address 172.16.2.3/31
nv set interface swp32 bridge domain br_default access 10
nv set interface vlan10 ipv4 address 10.0.10.1/24
nv set interface vlan10 type svi
nv set interface vlan10 vlan 10
nv set interface vlan10 vrf SERVICE_A
nv set nve vxlan source address 172.16.255.2
nv set nve vxlan state enabled
nv set router bgp autonomous-system 65002
nv set router bgp router-id 172.16.255.2
nv set router bgp state enabled
nv set router policy prefix-list local_l0_ip_address rule 10 action permit
nv set router policy prefix-list local_l0_ip_address rule 10 match 172.16.255.2/32
nv set system aaa class nvapply action allow
nv set system aaa class nvapply command-path / permission all
nv set system aaa class nvshow action allow
nv set system aaa class nvshow command-path / permission ro
nv set system aaa class sudo action allow
nv set system aaa class sudo command-path / permission all
nv set system aaa role nvue-admin class nvapply
nv set system aaa role nvue-monitor class nvshow
nv set system aaa role system-admin class nvapply
nv set system aaa role system-admin class sudo
nv set system aaa user cumulus full-name cumulus,,,
nv set system aaa user cumulus hashed-password '*'
nv set system aaa user cumulus role system-admin
nv set system api state enabled
nv set system config auto-save state enabled
nv set system control-plane acl acl-default-dos inbound
nv set system control-plane acl acl-default-whitelist inbound
nv set system docker state enabled
nv set system docker vrf mgmt
nv set system hostname leaf2
nv set system ntp
nv set system ssh-server state enabled
nv set system wjh channel forwarding trigger l2
nv set system wjh channel forwarding trigger l3
nv set system wjh channel forwarding trigger tunnel
nv set system wjh state enabled
nv set vrf SERVICE_A evpn state enabled
nv set vrf SERVICE_A evpn vni 10000
nv set vrf SERVICE_A router bgp address-family ipv4-unicast redistribute connected state enabled
nv set vrf SERVICE_A router bgp address-family ipv4-unicast state enabled
nv set vrf SERVICE_A router bgp address-family l2vpn-evpn state enabled
nv set vrf SERVICE_A router bgp autonomous-system 65002
nv set vrf SERVICE_A router bgp router-id 172.16.255.2
nv set vrf SERVICE_A router bgp state enabled
nv set vrf default router bgp address-family ipv4-unicast network 172.16.255.2/32
nv set vrf default router bgp address-family ipv4-unicast state enabled
nv set vrf default router bgp address-family l2vpn-evpn state enabled
nv set vrf default router bgp neighbor 172.16.1.2 peer-group EBGP_UNDERLAY_SPINES
nv set vrf default router bgp neighbor 172.16.1.2 type numbered
nv set vrf default router bgp neighbor 172.16.2.2 peer-group EBGP_UNDERLAY_SPINES
nv set vrf default router bgp neighbor 172.16.2.2 type numbered
nv set vrf default router bgp neighbor 172.16.255.253 peer-group EBGP_OVERLAY_SPINES
nv set vrf default router bgp neighbor 172.16.255.253 type numbered
nv set vrf default router bgp neighbor 172.16.255.254 peer-group EBGP_OVERLAY_SPINES
nv set vrf default router bgp neighbor 172.16.255.254 type numbered
nv set vrf default router bgp peer-group EBGP_OVERLAY_SPINES address-family l2vpn-evpn state enabled
nv set vrf default router bgp peer-group EBGP_OVERLAY_SPINES description EBGP_OVERLAY_SPINES
nv set vrf default router bgp peer-group EBGP_OVERLAY_SPINES multihop-ttl 5
nv set vrf default router bgp peer-group EBGP_OVERLAY_SPINES remote-as external
nv set vrf default router bgp peer-group EBGP_OVERLAY_SPINES update-source lo
nv set vrf default router bgp peer-group EBGP_UNDERLAY_SPINES address-family ipv4-unicast
nv set vrf default router bgp peer-group EBGP_UNDERLAY_SPINES description EBGP_UNDERLAY_SPINES
nv set vrf default router bgp peer-group EBGP_UNDERLAY_SPINES remote-as external
nv set vrf default router bgp state enabled
cumulus@leaf2:mgmt:~$
```

