# Instructions for Lab

## Task 1 
1. Change the hostname of the router to R1:
```plaintext
Router>enable
Router#config t
Router(config)#hostname R1
R1(config)#end
```
2. Change the hostname of the router to R1:
```plaintext
Router>enable
Router#config t
Router(config)#hostname R2
R2(config)#end
```
## Task 2 
1. Assign IP Address to serial 0/0/0 interface on router R1
```plaintext
R1>en
R1(config)#interface s0/0/0
R1(config-if)#ip add 172.16.1.1 255.255.255.192
R1(config-if)#no shut
```
2. Assign IP Address to serial 0/0/0 interface on router R2
```plaintext
R2>en
R2(config)#interface s0/0/0
R2(config-if)#ip add 172.16.1.2 255.255.255.192
R2(config-if)#no shut
```
3. Assign IP addresses to loopback interfaces on router R2 using the following configuration.
```plaintext
R2>en
R2(config)#interface lo10
R2(config-if)#ip add 10.10.10.3 255.255.255.128
R2(config-if)#exit
R2(config)#interface lo20
R2(config-if)#ip add 10.20.20.3 255.255.255.240
R2(config-if)#exit
R2(config)#interface lo30
R2(config-if)#ip add 10.30.30.3 255.255.255.248
R2(config-if)#end
```
## Task 3
1. Show all configured IP addresses on router R2
```plaintext
R2#show ip int brief
```
2. Display the subnet mask applied to the interface
```plaintext
R2#show interface s0/0/0
```