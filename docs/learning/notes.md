Inventory: The actually state of machine.
Decisions: What I choose, the options I discard and the why.
Runbook: step-by-step to rebuild the the Ubuntu Server.

---

In infra always use ISO 8601: `2026-06-09`

---

IdentityFile ~/.ssh/id_homelab      # What key use in host
IdentitiesOnly yes                  # Only use this key, don't offer any other.

---

If gonna commit something in `docs/`, use the convetional commit, `docs`.

---

```yml
network:
  version: 2          # versão do formato do Netplan (não é versão do IP)
  ethernets:          # bloco de interfaces cabeadas
    enp2s0:           # a interface que estamos configurando
```

```yml
dhcp4: false
dhcp6: false
```

"don't ask the addresses for anyone"

```yml
match:
  macaddress: f4:b5:20:0e:11:d6
set-name: enp2s0
```

"Find the motherboard where MAC is this, and put name enp2s0"

- P.S: Is not motherboard, is network card that are in motherboard, but for me now motherboard is more easy to remember.

```yml
addresses:
  - 192.168.0.50/24
```

/24 -> Quanto do endereço é rede?
192.168.0 -> Identificam a rede.
.50 -> Identifica a máquina.

```
routes:
  - to: default
    via: 192.168.0.1
```

anything out of 192.168.0.x, send to the router.

### IMPORTANT

```
nameservers:
  addresses: [1.1.1.1, 8.8.8.8]
```

How translate name in IP. Resolvers public, instead router.
Here we have a trade-off, and I want to understand more about it.

```
wakeonlan: true
```

keep the motherboard energy with the machine down.

- P.S: "motherboard" = "Network card"

```
The MAC address come from the network card, but how my network card is in motherboard the MAC addresse come from it.

If one day I put a PCIe in my Server, the MAC will come from it.
```

---

Note about interfaces.

Interaces names is not fixed! The Linux put a name like `enp2s0` depeding which slot the motherboard is connected. Because of this in wakeonlan we sent search for macaddress.

The macaddress don't change! Differently the interface name.

Name = where the motherboard sign.
MAC = What motheboard is.

---

Search for IPAM. Is the method that's big company's use to manage IPs.

---

## DHCP and the Pool

DHCP (Dynamic Host Configuration Protocol) is the service running on the
router that hands out IP addresses to devices that ask for one.

The **pool** is the range of addresses the DHCP server is allowed to hand
out. It is a setting you configure, not the protocol itself.

In my network (192.168.0.0/24) the pool is `.100` – `.199`.

This splits the network into two zones:

- **Inside the pool (.100 – .199) — automatic.**
  A device connects, asks for an address, and the router gives it a free one
  from this range. My Mac got `.168` this way. The address is leased, not
  owned: it can change (lease time here is 120 minutes).

- **Outside the pool (.2 – .99 and .200 – .254) — manual.**
  The router never hands these out. They are free for me to assign by hand
  on the machine itself. My server is `.50`, set in Netplan.

Special addresses in a /24:

- `.0` — the network address. Not usable by a host. Universal rule.
- `.255` — the broadcast address. Not usable by a host. Universal rule.
- `.1` — my router. This is a **convention**, not a rule. Some routers use
  `.254` or another address.

**The rule that matters:** an address I assign by hand must be outside the
pool. Otherwise the router could hand the same address to another device,
causing an intermittent IP conflict.
