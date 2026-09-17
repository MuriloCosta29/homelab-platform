# Inventory

## Server

- Hostname: star-platinum
- Vendor/model: BIOSTAR Group B360MHD PRO2
- CPU: Intel(R) Core(TM) i5-8400 CPU @ 2.80GHz
- RAM: 8gb | 2x memory of 4gb.
- Disk:
  - WDC WDS240G2G0A SSD, 223.6G physical
  - sda3: 220.5G LVM volume group
  - ubuntu--vg-ubuntu--lv: 100G, mounted at /
  - ~120G unallocated in the VG (Ubuntu installer default)
- Operating system: Ubuntu Server
- Ubuntu version: Ubuntu 26.04.1 LTS

## Network

- Router mode: router
- Local network: 192.168.0.0/24
- Gateway: 192.168.0.1
- Mac IP: 192.168.0.168
- Ubuntu Server IP: 192.168.0.50
- Ubuntu network interface: enp2s0
- DNS: `[1.1.1.1, 8.8.8.8]`

## Access

- Administrative user: murilo
- Deploy user: none yet
- SSH method: key (password auth still enable)
- SSH port: 22

## Router

192.168.0.1          gateway (roteador)
192.168.0.2  – .99   free for fixed IPs | The Ubuntu is here .50
192.168.0.100– .199  pool DHCP (Mac get .168)
192.168.0.200– .254  free for fixed IPs
192.168.0.0          Network Address
192.168.0.255        broadcast

## Known constraints

**Double NAT**

Infos:

Intelbras(Principal router).
TP-LINK Archer C6(Secundary router).

Intelbras(192.168.1.x) translate one time
↓
TP-LINK(192.168.0.x) Create a sub-net inside Intelbras network.
↓
That's make the network be translated two(2) times, generating a Double NAT.

More in [ADR-0003](./decisions/0003-why-i-choose-double-nat.md)

- For now, the ADR don't exist, but I'm writing it.
