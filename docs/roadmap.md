# Roadmap

## Phase 0: Inventory

- [ ] Document the server model.
- [ ] Document CPU, RAM, and disk.
- [ ] Document the network interface.
- [ ] Document the Mac IP.
- [ ] Document the planned Ubuntu Server IP.
- [ ] Document the gateway.
- [ ] Document the router mode: router or access point.

## Phase 1: Network

- [ ] Decide between DHCP reservation and static IP with Netplan.
- [ ] Make sure the Mac and Ubuntu Server are in the same subnet.
- [ ] Test `ping` from the Mac to the Ubuntu Server.
- [ ] Test internet access from Ubuntu by IP: `ping 1.1.1.1`.
- [ ] Test DNS from Ubuntu: `resolvectl query google.com`.
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


