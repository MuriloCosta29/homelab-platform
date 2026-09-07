# Runbook: First SSH Access

## Goal

Connect from macOS to the Ubuntu Server using the local IP address.

## Steps

1. Confirm the Ubuntu IP:

```bash
hostname -I
```

2. Test connectivity from macOS:

```bash
ping UBUNTU_IP
```

3. Connect:

```bash
ssh user@UBUNTU_IP
```

4. Confirm hostname:

```bash
hostname
```

5. Confirm operating system:

```bash
lsb_release -a
```

## Common Problems

- `Destination Host Unreachable`: wrong network, subnet, or gateway.
  - Look the `/etc/netplan/.yml`. I have problems with different gateways.
- `Connection refused`: SSH is not running or the port is blocked.
- `Permission denied`: wrong user, password, or key.
- Timeout: wrong IP, firewall, or host outside the network.

