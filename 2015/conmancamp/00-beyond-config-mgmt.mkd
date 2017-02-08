# Beyond Config Management
_Mitchell Hashimoto_

Not going to talk about tools or vendors. Interesting.

## Starting from 2006

### Datacenters
- No APIs.
- No elasticity.
- Monolithic machines.
   - Machines running lots of software.
- Very little IaaS/SaaS.

### Problems
- (Lack of) Uniformity of servers
- Scalable change management; how do you ensure that adding more
  servers/services only increases complexity sub-linearly.
- Auditing server state; how do you find/fix special snowflakes?
- Early service discovery.
   - How do load balancers get configured with webservers?

### Software
- Manual node (de)registration.
- Single master servers.
- Check/correct divergence.
- Agent model, usually Ruby.
   - Why is this important?

### The point?
- Problems closely tied to the solution.
- Datacenter + problems = software

The solutions were correct/right at the time. The question, however - is that
design of software going to work today?

## The future!
### Datacenters
- API driven
- Highly elastic (particularly for stateless services)
- Small, single purpose servers.
   - Less coupling.
- SaaS for core infrastructure
   - DNS, monitoring, etc etc etc
- Virtualisation and containers.

### Problems
- Infrastructure creation/deletion
   - As we're becoming more elastic, we need a way to create infrastructure
     than just using vendor API. (CRUD)
- Service discovery.
   - Where is everything? Need to know *now*.
- SaaS management
   - There is no future with fewer servers. (Luke)
   - There is no future with absolutely less servers, but possibly you are
     running less of them yourself. (Hashi)
- Layer cake management
   - Openstack.
   - Virtualisation.
   - (Composability)
- Faster, more real time change.
- These are more interesting than basic config management.

### Software
- Datacenters + problems = ?
- No crystal ball.
- Distributed systems.
- Failure expectation/tolerance.
   - Apart from monitoring, most software shouldn't care if stuff disappears.
- API driven and managed.
   - Planned API, rather than an artefact/side effect of architecture of
     software.
- Low resource usage for scale.
   - How many Ruby monitoring agents do you run on a server with 100 containers
     on it?
- Interaction with SaaS.
- VMs and containers.

Build out vs build up

Build up: build upon existing stuff.
Build out: build new tools that are solving specific problems.

### Which is better?
- For consumers?
- For vendors?

## Left out
- SDN
- Software defined storage.
- Left out for people going very deeply in to containers.
