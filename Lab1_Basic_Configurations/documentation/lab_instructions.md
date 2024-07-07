# Instrukcje do Lab 1

## Krok 1: Podstawowa konfiguracja przełącznika
1. Skonfiguruj hasło do konsoli:
    ```plaintext
    Switch> enable
    Switch# configure terminal
    Switch(config)# line console 0
    Switch(config-line)# password cisco_console
    Switch(config-line)# login
    Switch(config-line)# exit
    ```

2. Skonfiguruj hasło do uprzywilejowanego trybu:
    ```plaintext
    Switch(config)# enable secret cisco_enable
    ```

## Krok 2: Utworzenie VLAN-ów
1. Utwórz VLAN 10:
    ```plaintext
    Switch(config)# vlan 10
    Switch(config-vlan)# name Sales
    Switch(config-vlan)# exit
    ```

2. Utwórz VLAN 20:
    ```plaintext
    Switch(config)# vlan 20
    Switch(config-vlan)# name Engineering
    Switch(config-vlan)# exit
    ```

3. Utwórz VLAN 30:
    ```plaintext
    Switch(config)# vlan 30
    Switch(config-vlan)# name HR
    Switch(config-vlan)# exit
    ```

## Krok 3: Konfiguracja interfejsów VLAN
1. Skonfiguruj interfejs VLAN 10:
    ```plaintext
    Switch(config)# interface vlan 10
    Switch(config-if)# ip address 192.168.10.1 255.255.255.0
    Switch(config-if)# no shutdown
    Switch(config-if)# exit
    ```

2. Skonfiguruj interfejs VLAN 20:
    ```plaintext
    Switch(config)# interface vlan 20
    Switch(config-if)# ip address 192.168.20.1 255.255.255.0
    Switch(config-if)# no shutdown
    Switch(config-if)# exit
    ```

3. Skonfiguruj interfejs VLAN 30:
    ```plaintext
    Switch(config)# interface vlan 30
    Switch(config-if)# ip address 192.168.30.1 255.255.255.0
    Switch(config-if)# no shutdown
    Switch(config-if)# exit
    ```

## Krok 4: Konfiguracja interfejsów VLAN
1. DHCP dla VLAN 10:
    ```plaintext
    Switch(config)# ip dhcp pool VLAN10
    Switch(dhcp-config)# network 192.168.10.0 255.255.255.0
    Switch(dhcp-config)# default-router 192.168.10.1
    Switch(dhcp-config)# dns-server 8.8.8.8
    Switch(dhcp-config)# exit
    ```

2. DHCP dla VLAN 20:
    ```plaintext
    Switch(config)# ip dhcp pool VLAN20
    Switch(dhcp-config)# network 192.168.20.0 255.255.255.0
    Switch(dhcp-config)# default-router 192.168.20.1
    Switch(dhcp-config)# dns-server 8.8.8.8
    Switch(dhcp-config)# exit
    ```

3. DHCP dla VLAN 30:
    ```plaintext
    Switch(config)# ip dhcp pool VLAN30
    Switch(dhcp-config)# network 192.168.30.0 255.255.255.0
    Switch(dhcp-config)# default-router 192.168.30.1
    Switch(dhcp-config)# dns-server 8.8.8.8
    Switch(dhcp-config)# exit
    ```

## Krok 5: Przypisanie portów do VLAN-ów
1. Przypisanie portu do VLAN 10:
    ```plaintext
    Switch(config)# interface range fa0/1 - 8
    Switch(config-if-range)# switchport mode access
    Switch(config-if-range)# switchport access vlan 10
    Switch(config-if-range)# exit
    ```

2. Przypisanie portu do VLAN 20:
    ```plaintext
    Switch(config)# interface range fa0/9 - 16
    Switch(config-if-range)# switchport mode access
    Switch(config-if-range)# switchport access vlan 20
    Switch(config-if-range)# exit
    ```
3. Przypisanie portu do VLAN 30:
    ```plaintext
    Switch(config)# interface range fa0/17 - 24
    Switch(config-if-range)# switchport mode access
    Switch(config-if-range)# switchport access vlan 30
    Switch(config-if-range)# exit
    ```
