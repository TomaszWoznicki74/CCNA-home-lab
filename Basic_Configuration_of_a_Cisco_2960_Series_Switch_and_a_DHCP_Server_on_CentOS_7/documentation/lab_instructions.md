# Instructions for Lab 3

## Step 1: Connect the Console Cable to the Switch
1. Connect one end of the console cable to the switch's console port and the other end to your computer.

## Step 2: Establish a Connection to the Switch Using PuTTY

1. Open PuTTY and configure the connection type to "Serial".

2. Set the correct COM port and speed (typically 9600).



## Step 3: Switch Configuration
1. Create VLAN 10 and VLAN 20
    ```plaintext
    Switch>enable
    Switch#configure terminal
    Switch(config)#vlan 10
    Switch(config)#name VLAN10
    Switch(config)#vlan 20
    Switch(config)#name VLAN20
    ```

## Step 4: Assign IP Address to VLAN 10 Interface
    Switch(config)#interface vlan 10
    Switch(config-if)#ip address 10.10.100.5 255.255.255.0
    Switch(config-if)#no shutdown
    Switch(config-if)#exit

## Step 5: Configure all switch ports to access mode, shut them down, and add to VLAN 20
    Switch(config)#interface range fa0/1 - 24
    Switch(config-if)#switchport mode access
    Switch(config-if)#switchport access vlan 20
    Switch(config-if)#shutdown
    Switch(config-if)#exit

## Step 6: Assign ports fa0/1-4 to VLAN 10 and enable them
    Switch(config)#interface range fa0/1 - 4
    Switch(config-if)#switchport access vlan 10
    Switch(config-if)#no shutdown
    Switch(config-if)#exit 

# Validation for Lab 3

## Step 1: Verify APIPA on Windows Machines Before Starting the DHCP Server

1. Ensure that the Windows hosts are connected to the network.

2. Check if the Windows machines receive IP addresses in the range of 169.254.x.x (APIPA range).

## Step 2: Enable the DHCP Server and Verify Dynamic IP Assignment

1. Start the DHCP server
    ```plaintext
    sudo systemctl start dhcpd
    ```

2. Check if the Windows hosts receive IP addresses in the range specified in the DHCP configuration (10.10.100.10 to 10.10.100.254).


This documentation provides detailed steps for configuring a Cisco 2960 series switch and setting up a DHCP server on a CentOS 7 machine, as well as validating the functionality of APIPA and DHCP-based IP address assignment for Windows hosts in a LAN environment.