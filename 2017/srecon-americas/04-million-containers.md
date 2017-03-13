# A million containers isn't cool

- Containers in the small.

## Who are gocardless?
- High $ / request.
- Reliability is key

## Deploy software reliably
- How containers help
- Other options

## Deployment artefacts
- Source code --> something you can put on your servers.
- JAR files.
- Statically linked binaries.
- OS packages (.deb, .rpm)

### Some languages are better than others
- Ruby.
- Typical deployment flow is capistrano
  - Clone
  - Build deps <-- hope
  - Run schema migrations
  - Build static assests <-- hope
  - SIGHUP <-- hope

### What's wrong with it?
- Hope is not a desirable property in a software system.

### Applications don't run in a vacuum
- Ruby app
- Ruby dependencies (Nokogiri)
- Native libraries (libxml2)

## How do we install software?
- Nokogiri --> bundler
- libxml2 --> apt get
- Normally controlled by two different systems.
  - App source control
  - OS level puppet/chef.
- If they're defined separately, you're going to  have a bad time

## Container images
- Deployable unit.
- This is why most companies should care about Docker.
- They don't care about namespaces/cgroups, they use images.
- Docker is a fat-jar for people not using the JVM.

## How did containers help?
- What did we care about?

### Uniform deployment
- Concrete definition of a deployable unit.
- Build artefacts. Teams manage their own.
- Fail early.
  - Do as much during build as possible.

### What did we *not* care about?
- Distributed scheduler.
  - Nothing comes for free.

### Kubernetes
- You need to understand
  - Distributed scheduler
  - Cluster DNS
  - etcd

## What did gocardless build?

### Service definition
- Container image.
- Environment config.
- Command to run.
- Resource limits.
- ...
- This is a config management problem
  - Put it in Chef!

### Single node orchestration
- conductor
  - Service ID
  - Git revision
- Flow
  - Start containers for new versions.
  - Wait for L7 healthcheck.
  - Rewrite local nginx config.
  - Reload nginx
  - Stop old containers
  - Question: how do you define "happy everything that's settled"?

### What about cron jobs?
- Similar.
- Source contains normal cron file.
- Conductor wraps/containerise it.

### Deployment
- Capistrano
- Kept deployment consistent from old/new.
- Help developers do their jobs.

## But processes die
- supervisor
- e.g.
  - upstart
  - systemd
  - runit
- None of those played well with docker
- Docker restart policies were really annoying.
- All of these were hard to stop.
  - Docker stop takes a container ID, which is changing every few milli.
- Restart policies
  - Hard limit. Not hard restart limit per time period.

### We built a process supervisor
- conductor supervise
  - simple and naive
  - number of running containers
  - health check each container
    - Process running != doing useful work.
  - Restart if either fails
  - Rate limit at most every 5 seconds
    - If there's a pending restart, all checks are deferred.
- Can disable "conductor supervise" in upstart
- We don't want this. Hopefully other stuff will get better.

## Other options
- systemd + rkt
  - Conductor generate systemd config
  - Systemd manages processes
  - Delete conductor supervise
  - HTTP health checks????
- VMs + autoscaling
  - Google, Amazon have this already.
- Packer
  - Builds images.
  - Slower than doing it with containers.

## Meta thoughts
- Thought leader emoji

### Introduce new infrastructure where failure is survivable
- Canary with low risk stuff.
  - Non critical batch
  - Background workers
  - API servers

### Goal state is what matters
- Everything might change before your next method call

### Systems are not useful without context
- Nothing matters without business awareness.
- Pare stuff down to solve problems for your company.

## Questions
- Are you going to revisit the lack of a distributed scheduler?
  - Advancement of those tools to be easier to use? (or managed by someone
    else)
    - Hosted Kubernetes etc.
  - Our needs approaching from the other side.
- Are 5 second healthchecks too long? How does your loadbalancer work?
  - We're doing a similar thing at HAProxy. Can each host run with useful
    content.
  - Retry is handled in client libraries.
- How do you monitor those containers?
  - Sensu? Still evolving.
- Mapping containers to machines?
  - Big wedge of JSON?
- Process restart, everything on machine?
