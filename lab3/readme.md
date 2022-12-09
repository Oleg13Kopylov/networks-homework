## Описание модернизации сети

К лаборатории из папки lab1 (она соответствует первому домашнему заданию) были применены следующие изменения:

**На R7:**
```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#interface e0/0
Router(config-if)#no shutdown
Router(config-if)#ip addres
*Dec  9 13:38:00.738: %LINK-3-UPDOWN: Interface Ethernet0/0, changed state to up
*Dec  9 13:38:01.743: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to up
Router(config-if)#ip address 100.0.10.2 255.255.255.0
Router(config-if)#exit
Router(config)#exit
Router#
*Dec  9 13:38:22.065: %SYS-5-CONFIG_I: Configured from console by console
Router#wr
Building configuration...
[OK]
```

**На R4:**
```
Router>enable
Router#configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#ip dhcp excluded-address 10.0.10.1 10.0.10.10
Router(config)#ip dhcp excluded-address 10.0.20.1 10.0.20.10
Router(config)#ip dhcp pool right_network                   
Router(dhcp-config)#default-router 10.0.20.1
Router(dhcp-config)#dns-server 10.0.20.2
Router(dhcp-config)#network 10.0.20.0 255.255.255.0
Router(dhcp-config)#exit
Router(config)#ip dhcp pool left_network                    
Router(dhcp-config)#default-router 10.0.10.1       
Router(dhcp-config)#dns-server 10.0.10.2           
Router(dhcp-config)#network 10.0.10.0 255.255.255.0
Router(dhcp-config)#exit
Router(config)#access-list 100 permit ip 10.0.10.0 0.0.0.255 any
Router(config)#access-list 100 permit ip 10.0.20.0 0.0.0.255 any
Router(config)#$ MY_POOL 100.0.10.10 100.0.10.250 netmask 255.255.255.0       
Router(config)#
*Dec  9 13:45:13.948: %LINEPROTO-5-UPDOWN: Line protocol on Interface NVI0, changed state to upi
Router(config)#interface e0/1
Router(config-if)#no shutdown
Router(config-if)#ip address 
*Dec  9 13:45:36.354: %LINK-3-UPDOWN: Interface Ethernet0/1, changed state to up
*Dec  9 13:45:37.364: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/1, changed state to up
Router(config-if)#ip address 100.0.10.1 255.255.255.0
Router(config-if)#ip nat outside
Router(config-if)#exit
Router(config)#interface e0/0                     
Router(config-if)#no shutdown
Router(config-if)#ip nat inside
Router(config-if)#exit
Router(config)#interface e0/0.10
Router(config-subif)#no shutdown
Router(config-subif)#ip nat inside    
Router(config-subif)#exit
Router(config)#interface e0/0.20
Router(config-subif)#no shutdown      
Router(config-subif)#ip nat inside    
Router(config-subif)#exit
Router(config)#ip nat inside source list 100 pool MY_POOL
Router(config)#exit
Router#
*Dec  9 13:49:12.543: %SYS-5-CONFIG_I: Configured from console by console
Router#wr
Building configuration...
[OK]
```

## Скриншоты
![telegram-cloud-photo-size-2-5231445955700704046-x](https://user-images.githubusercontent.com/55313421/206730623-b4e6251b-b28c-41c4-99af-bc88c937507d.jpg)

![telegram-cloud-photo-size-2-5231445955700704048-y](https://user-images.githubusercontent.com/55313421/206730826-b2ceb2b5-d5f1-4671-9120-267af57f8707.jpg)


