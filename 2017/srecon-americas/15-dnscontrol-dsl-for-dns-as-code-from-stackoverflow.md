# DNSControl: A DSL for DNS as Code from stackoverflow.com

## DNS at stack overflow
- Lots of domains
- Many sites
- Tons of records
- Hosted all over the internet. (6 providers)
- Multiple datacenters (2 plus "the cloud")

## Artisanal, Hand Crafted Zone file
- Manual change is difficult and risky
- Datacenter failover is a DNS zonefile update. (!!!)

## The cloud
- Not just on premise
- Multiple DNS providers
- All have different ways of managing DNS

### Web DNS panels suck
- Not repeatable
- Lock in
- No revision control
- Attribution
- Authorisation

### All have APIs
- \o/
- All different APIs.
  - /o\

## DNS control
- Language/compiler for DNS specifications.
- Javascript DSL.
- Allows preview.
- Supports many providers.

## Cool tricks
- Subnets as variables.
- All the variables!
- String concatenation.
- Google Apps MX records.

## Applications
### Changing DNS providers.
- Avoids lock in.
- Resilience to single-provider outages
  - http://bit.ly/StackDualDNS

### Transforms
- Turning CDN on/off
  - Conditional.
- Make changes more boring and less tricky.

### Integrated cloud features
- Metadata for e.g. Cloudflare proxying.

## Implementation details
- 6k SLOC of golang

### Why javascript?
- Don't write your own language.
- Native go interpreter
- All power of real language, no maintenance burden.
- Javascript functions build data structures that become our IR.
- IR is the desired state.

## If you have a DSL, have an IR!
- Yes. This.
- DSL generates object models which can be canonicalised, reasoned about and
  tested.
- Makes providers very simple.
-
## Modular design
- No special cases.
- Core code ignorant of provider features.
- DSL and common packages are general purpose.
- Provider implementations handle details and oddities.
- Keep core extensible.

## Operator benefits
- Don't need to learn the quirks of each provider.
- Examples
  - Dots, no dots.
  - FQDN, or just host part.
  - Separate MX priority field?
- Automation does the hard part.
- Lowers the barrier to entry, safely

## CI for DNS
- Preview locally, push through CI after merging pull request.

## Current state
- Implementation for 10 providers.
- No DNSSEC yet.
- Warning about domain expiration.

## Questions
- IPv6?
- Import tool?
