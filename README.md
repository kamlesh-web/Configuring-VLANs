  # Configuring-VLANs
  Switch>
  Switch>
  Switch>enable
  Switch#
  	
  Switch#show interfaces status
  Port      Name               Status       Vlan       Duplex  Speed Type
  Fa0/1                        connected    1          a-full  a-100 10/100BaseTX
  Fa0/2                        connected    1          a-full  a-100 10/100BaseTX
  Fa0/3                        connected    1          a-full  a-100 10/100BaseTX
  Fa0/4                        connected    1          a-full  a-100 10/100BaseTX
  Fa0/5                        connected    1          a-full  a-100 10/100BaseTX
  
  (trancated...)
  
  Gig0/1                       notconnect   1          auto    auto  10/100/1000BaseTX
  Gig0/2                       connected    1          a-full  a-100 10/100/1000BaseTX
  
  Switch#
  Switch#
  Switch#configure terminal
  Enter configuration commands, one per line.  End with CNTL/Z.
  Switch(config)#
  Switch(config)#hostname Switch1
  Switch1(config)#
  Switch1(config)#enable secret CCNA
  Switch1(config)#
  Switch1(config)#interface range f0/6-24
  Switch1(config-if-range)#
  Switch1(config-if-range)#description ##Not in use##
  Switch1(config-if-range)#
  Switch1(config-if-range)#shutdown
  
  %LINK-5-CHANGED: Interface FastEthernet0/6, changed state to administratively down
  
  %LINK-5-CHANGED: Interface FastEthernet0/7, changed state to administratively down
  
  (trancated...)
  
  Switch1(config-if-range)#
  Switch1(config-if-range)#	
  Switch1(config-if-range)#interface range f0/1-2
  Switch1(config-if-range)#
  Switch1(config-if-range)#switchport mode access
  Switch1(config-if-range)#
  Switch1(config-if-range)#switchport access vlan 120
  % Access VLAN does not exist. Creating vlan 120
  Switch1(config-if-range)#
  Switch1(config-if-range)#
  Switch1(config-if-range)#interface range f0/3-5
  Switch1(config-if-range)#
  Switch1(config-if-range)#switchport mode access
  Switch1(config-if-range)#
  Switch1(config-if-range)#switchport access vlan 150
  % Access VLAN does not exist. Creating vlan 150
  Switch1(config-if-range)#
  Switch1(config-if-range)#
  Switch1(config-if-range)#vlan 120
  Switch1(config-vlan)#
  Switch1(config-vlan)#name FINANCE
  Switch1(config-vlan)#
  Switch1(config-vlan)#vlan 150
  Switch1(config-vlan)#
  Switch1(config-vlan)#name IT
  Switch1(config-vlan)#
  Switch1(config-vlan)#
  %LINK-3-UPDOWN: Interface GigabitEthernet0/2, changed state to down
  
  %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/2, changed state to down
  
  %LINK-5-CHANGED: Interface GigabitEthernet0/2, changed state to up
  
  %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/2, changed state to up
  
  Switch1(config-vlan)#
  Switch1(config-vlan)#interface g0/2
  Switch1(config-if)#
  Switch1(config-if)#switchport mode trunk
  
  Switch1(config-if)#
  %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/2, changed state to down
  
  %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/2, changed state to up
  
  Switch1(config-if)#
  Switch1(config-if)#switchport trunk allowed vlan 120,150
  Switch1(config-if)#
  Switch1(config-if)#do write
  Building configuration...
  [OK]
  Switch1(config-if)#
  Switch1(config-if)#do show vlan brief
  
  VLAN Name                             Status    Ports
  ---- -------------------------------- --------- -------------------------------
  1    default                          active    Fa0/6, Fa0/7, Fa0/8, Fa0/9
                                                  Fa0/10, Fa0/11, Fa0/12, Fa0/13
                                                  Fa0/14, Fa0/15, Fa0/16, Fa0/17
                                                  Fa0/18, Fa0/19, Fa0/20, Fa0/21
                                                  Fa0/22, Fa0/23, Fa0/24, Gig0/1
  120  FINANCE                          active    Fa0/1, Fa0/2
  150  IT                               active    Fa0/3, Fa0/4, Fa0/5
  1002 fddi-default                     active    
  1003 token-ring-default               active    
  1004 fddinet-default                  active    
  1005 trnet-default                    active    
  Switch1(config-if)#
  Switch1(config-if)#
