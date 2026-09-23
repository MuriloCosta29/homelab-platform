# AI-0001: Deciding between DHCP and static IP without understanding networking

**Date:** 2026-09-15  
Related: [ADR-0002](../decisions/0002-dhcp-and-static-ip-in-netplan.md)

## Context

I was closing this task in the roadmap:

- [x] Decide between DHCP reservation and static IP with Netplan.

The task was already marked as done, because the static IP was already
configured in `/etc/netplan/` — but I had configured it months ago with GPT,
not in this project, and I could not explain it.

## What I asked

"I want you to help me understand the difference between DHCP and Netplan
in the machine."

## What AI gave

Claude answered as if the decision was already made: "you decided static IP
via Netplan over DHCP".

I noticed it was wrong and pushed back:

"No, I didn't choose! Explain this to me."

Then it explained the real difference: both options give a fixed IP; what
changes is where the configuration lives — in the machine (Netplan, in Git,
reproducible with Ansible) or in the router (DHCP reservation, outside Git,
and depending on a dashboard I barely have access to).

## What I did with it

I wrote [ADR-0002](../decisions/0002-dhcp-and-static-ip-in-netplan.md) with
context, decision, discarded alternatives and consequences.

But when I finished it, I felt something was wrong: **I felt like I really
didn't understand what I had done.**

## Did I learn?

Partially.

I understood the decision, and I can defend it. But I did not understand the
ground under it. That is why the explanation kept branching — DHCP led to
pool, pool led to subnet, subnet led to broadcast — and every new term
arrived without a place to land.

So I asked what I actually needed to study for this project:

```
Ports, TCP and UDP — my biggest real gap.
IP addressing and subnetting — consolidates what I half know.
DNS — how a name becomes an IP.
NAT — I already live with double NAT.
Routing — routing table, most specific route wins, default gateway.
Troubleshooting tools — ping, traceroute, dig, netstat/ss, tcpdump.
```

## Roadmap

[Click here](../learning/networking-roadmap.md)
