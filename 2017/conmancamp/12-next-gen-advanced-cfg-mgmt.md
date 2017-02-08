# MGMT advanced

## mgmtconfig
- Patches needed.

## metaparams
- Per resource

### Noop
- NOOP resource dos nothing.
- noop meta param works.

### Retry/delay
- Retry max num of failures (or -1)
  - default
- delay min ms between retries
- Watch & CheckApply
- Currently the same, don't need different numbers.
- No global yet.
- Everything idempotent except exec

### Limit/burst
- Max # events per second
- Allow # of extra events as a burst
- todo, reciprocal
- Coalesces (in head); while operation in progress and rate limit tripped,
  events dropped (on a per resource basis).

### Poll
- Replaces watch
- Occasionally useful
- Avoids code duplication in resources.
- TODO: Replace exec poll metaparam
- (More of a crutch, but not everything is like systemd and generates events)

## Automatic edges
- packagekit library
  - abstracts away all the backends
  - provides events when they change
  - know what files are in the package
  - look in it to see if the service file exists in the package and the service
    is defined.

## Automatic grouping: graph
- Analyse graph, group them into a single resource.
- (e.g. invoke apt-get once for all missing packages)
- Can be enabled/disabled per resource.

## Embedding mgmt
- libmgmt
- general graph library

## Refresh
- Notification along graph dependencies.
  - Every edge can specify "refresh" as a bool.

## Send->recv
- data transfer along graph edges
  - every time you shell out, you're doing something wrong.
- Map the output of one resource to the input of another.
- Machine local. Saves needing to have different resources read and write to
  files.

## timers
- Send events.

## Resources
- Resource guide. Write new resources, build existing ones.
