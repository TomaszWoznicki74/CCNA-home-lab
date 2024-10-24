# Instructions for Lab 2

## Step 1: Change Switch Hostname
1. Change the hostname of the switch to SW1:
    ```plaintext
    Switch> enable
    Switch# configure terminal
    Switch(config)# hostname SW1
    ```

## Step 2: Create Users
1. Create a user with privilege level 15 and password "cisco":
    ```plaintext
    SW1(config)# username admin privilege 15 secret cisco
    ```
2. Create a user with privilege level 0 and password "user1234":
    ```plaintext
    SW1(config)# username user1 privilege 0 secret user1234
    ```

## Step 3: SSH Configuration
1. Set the domain name for SSH:
    ```plaintext
    SW1(config)# ip domain-name SSH_TEST
    ```
2. Generate RSA key with 1024-bit size:
    ```plaintext
    SW1(config)# crypto key generate rsa
    How many bits in the modulus [512]: 1024
    ```
3. Set SSH version to 2:
    ```plaintext
    SW1(config)# ip ssh version 2
    ```

## Step 4: Console Line Configuration
1. Configure the console line to use local login:
    ```plaintext
    SW1(config)# line console 0
    SW1(config-line)# login local
    SW1(config-line)# exit
    ```

## Step 5: VTY Line Configuration
1. Check the number of VTY lines on the switch:
    ```plaintext
    SW1# show running-config | include line vty
    ```
2. Configure VTY lines to use local login and allow only SSH:
    ```plaintext
    SW1(config)# line vty 0 15
    SW1(config-line)# login local
    SW1(config-line)# transport input ssh
    SW1(config-line)# exit
    ```

## Step 6: DHCP Server Configuration
1. Exclude IP addresses from 1 to 10 in the 192.168.1.0 network:
    ```plaintext
    SW1(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
    ```
2. Create a DHCP pool named "Poolvlan1":
    ```plaintext
    SW1(config)# ip dhcp pool Poolvlan1
    SW1(dhcp-config)# network 192.168.1.0 255.255.255.0
    SW1(dhcp-config)# default-router 192.168.1.1
    SW1(dhcp-config)# dns-server 8.8.8.8
    SW1(dhcp-config)# exit
    ```

## Step 7: VLAN 1 Configuration
1. Set the IP address for VLAN 1 to 192.168.1.5:
    ```plaintext
    SW1(config)# interface vlan 1
    SW1(config-if)# ip address 192.168.1.5 255.255.255.0
    SW1(config-if)# no shutdown
    SW1(config-if)# exit
    ```

## Step 8: Verify DHCP IP Assignment for Two PCs
1. Connect two PCs to the switch and verify they receive IP addresses from the DHCP server:
    - On each PC, use the `ipconfig` (Windows) or `ifconfig` (Linux/Mac) command to check the assigned IP address.

## Step 9: Test Remote SSH Connection
1. Connect to the switch remotely using SSH and verify correct login with valid credentials:
    - Use an SSH client (e.g., PuTTY or `ssh` command in the terminal):
        ```plaintext
        ssh admin@192.168.1.5
        ```
    - Enter the password when prompted.
2. Attempt to log in using incorrect credentials and verify access is denied:
    - Use an SSH client to attempt connection with invalid username or password:
        ```plaintext
        ssh invalid_user@192.168.1.5
        ```
    - Verify that access is denied.
