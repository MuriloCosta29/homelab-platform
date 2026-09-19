# Roadmap

## Phase 0: Inventory

- [x] Document the server model.
- [x] Document CPU, RAM, and disk.
- [x] Document the network interface.
- [x] Document the Mac IP.
- [x] Document the planned Ubuntu Server IP.
- [x] Document the gateway.
- [x] Document the router mode: router or access point.

## Phase 1: Network

- [x] Decide between DHCP reservation and static IP with Netplan.
- [x] Make sure the Mac and Ubuntu Server are in the same subnet.
- [x] Test `ping` from the Mac to the Ubuntu Server.
- [x] Test internet access from Ubuntu by IP: `ping 1.1.1.1`.
- [x] Test DNS from Ubuntu: `resolvectl query google.com`.
- [ ] Record the final configuration in `docs/inventory.md`.
- [ ] Write a learning note explaining DHCP, Netplan, gateway, subnet, and DNS.
- [ ] Draft the first blog post.

## Phase 2: SSH

Decision recorded in `docs/decisions/0001-dedicated-ssh-key.md`.

- [ ] Install and enable OpenSSH Server.
- [ ] Create an SSH key on the Mac if needed.
- [ ] Copy the public key to Ubuntu.
- [ ] Test SSH with key authentication.
- [ ] Disable root SSH login.
- [ ] Disable password authentication after key login is confirmed.
- [ ] Record the procedure in `docs/runbooks/ssh-access.md`.
- [ ] Write a blog post about secure remote access.
