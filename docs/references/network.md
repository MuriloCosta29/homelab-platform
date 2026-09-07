# Network

## Goal

Keep the Mac and Ubuntu Server on the same local network for stable SSH access.

## Commands On macOS

```bash
ipconfig getifaddr en0  -> Take private IP of my local network/Wi-Fi
route -n get default -> gateway
scutil --dns -> Shows which DNS servers the Mac is using.
```

## Commands On Ubuntu

```bash
ip addr -> IP, MAC address
ip route -> gateway
hostname -I -> Show all local IPs address
resolvectl status -> Active DNS configuration, and resolvers
```

## Rules

- The Ubuntu IP must not be the same as the Mac IP.
- The Ubuntu gateway should be the router IP for the local network.
- DNS can use public resolvers such as `1.1.1.1` and `8.8.8.8`.
- SSH by IP does not require DNS.
- SSH by hostname requires name resolution.

## Static IP Example With Netplan

```yaml
network:
  version: 2
  ethernets:
    enp3s0:
      dhcp4: false
      addresses:
        - 192.168.0.50/24
      routes:
        - to: default
          via: 192.168.0.1
      nameservers:
        addresses:
          - 1.1.1.1
          - 8.8.8.8
```

## Validation

On Ubuntu:

```bash
ping 1.1.1.1
resolvectl query google.com
```

On macOS:

```bash
ping 192.168.0.50
ssh user@192.168.0.50
```

## The because of validation

`ping 1.1.1.1`
  - Prove that exist a route to internet. `gateway, route and NAT`.

`resolvectl query google.com`
  - Prove only one things.
    - The server can translate **name** in **ip**.

