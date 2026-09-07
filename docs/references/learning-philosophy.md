# Learning Philosophy

## Learning Loop

1. Start with a real operational problem.
2. Ask what the unknown terms mean.
3. Research the options.
4. Pick the simplest correct approach.
5. Implement it manually.
6. Document what happened.
7. Turn the stable process into automation. BUT, only have automation, after really learn.
8. Write a blog post explaining the reasoning.

## Example: DHCP vs Netplan

Initial question:

```text
What do DHCP and Netplan even mean?
```

Learning flow:

- Understand DHCP as automatic network configuration.
- Understand Netplan as Ubuntu's network configuration layer.
- Compare DHCP reservation with a static IP.
- Choose based on the real router constraints.
- Validate with `ping`, `ip route`, and SSH.
- Document the final network setup.
- Write a blog post about the decision.
  - [Blog post](https://murilocosta29.github.io/blog/pausing-system-monitor-for-homelab/
)
