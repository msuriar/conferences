# Habitat

## Intro
- app.habitat.sh
  - origin/package
    - e.g nathenharvey/mongodb

```
$ sudo hab start nathenharvey/mongodb
$ ls /hab/pkgs/nathenharvey/mongodb/
```

- builds are versions.
- New version number and build number (timestamp) on every build.
- Not reproducible builds.

- written in rust

- can pass in configuration overrides for applications via `HAB_` environment
  variables.

## Supervisor

### Topologies
- supervisors run a gossip protocol between them.
- supervisors are topology aware e.g.
  - leader/follower (master election)
  - stand alone

### Management
- Habitat supervisor has REST API.
  - Creates standard REST endpoints proxied through the supervisor.
  - /services/{package}/{service_group}/health
  - /services/{package}/{service_group}/config
  - Enables standardised management.

### Update strategies
- All at once
- One at a time
- Progressive (exponential)
- Note, update fails, doesn't unwedge the canary.

# how to create stuff
- plan.sh
  - How to build a package.
  - Runtime, build dependencies
  - What artefacts turn up.
- Build in a cleanroom.
  - habitat studio
  - Post process packages
    - ACI
    - Docker
    - Mesosphere
    - Tarball
  - Output is: build output + supervisor
