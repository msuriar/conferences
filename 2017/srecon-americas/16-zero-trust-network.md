# Zero trust networks

## Pagerduty
- Pagerduty availability is high.
- Multiple datacenter.
- Active/active.
- Third party networks between datacenters.
- Need authn/authz.
- Aiming to implement access control first.
- Cross cloud, cross region.

### iptables
- o_O
- inside Chef
- Custom LWRP in Chef to create iptables rules.
- Allow machines/containers with specific roles to connect to other people.

### Now privacy
- IPsecVPN?
- Site to site tunnels. Annoying.
- Some providers don't provide VPC. So you then need to do hub and spoke.
- Raw IPsec in transport mode, full mesh.
  - dial on demand
- Strong VPN security.

## Assertion
- All flows are authenticated.
- All flows are authorized.
- No inherent value in an IP address.

## Properties
- No centralised firewalls.
- No network gateway
- No private network

## BeyondCorp
- Cool.

## The book
- Zero Trust Networks (O'Reilly)
- No trust in network

### Philosophy
- Don't use network position as a means of authenticating/authorising traffic.
- Becomes a forcing function to distribute policy enforcement throughout the
  network.
- Every flow is expected.
- Symbolic policy.
- Network agent.
  - Policy is against user + endpoint their connecting from.
- Automate policy.

### Benefits
- Visibility

## Advice
- Start early gathering data about what expected flows etc are.
  - Integrate into enforcement, sweet.

## Current state
- Still mostly roll your own.
- Trend towards repeatability, but it's not going to be as simple as building a
  perimeter network.

### Client side deployments
- Coca cola, Mazda - software defined security. (Wat?)
  - Rapid provisioning of branch offices. (Coke)
  - Mazda (all cars phone home)
- Google

## Questions
- Key management.
