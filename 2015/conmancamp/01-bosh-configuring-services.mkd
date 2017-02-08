_Andrew Clay Shafer_

# Why BOSH?
- Cloud foundry
   - Spaghetti components.
- Started at VMWare, spun out into Pivotal, some ex-Google SRE.
- Platform-as-a-Service; whatever that is.
   - An API that allows a developer to deploy code.

# What is BOSH?
- How does Google deploy AppEngine? How does Heroku deploy Heroku?
- If you wish to deploy a distributed system from scratch, you must first
  deploy the universe.
- Continuous integration.

# Rant
- Configuration management != writing installers.

# Need to manage a large scale distributed system
- Release engineering, deployment, etc etc
- Config management is necessary but not sufficient.

# Rant
- Trying to manage containers live VMs misses the point.

# BOSH is ...
- ... a distributed package and process orchestrator.
- Packages and processes
- Idempotent resource abstractions for fun and profit
   - Desired vs current stat.
- BOSH is **service** centric, not **server** centric.

# Primitives
- Highest level is "deployment".
- Lets you move deployments across providers.
- Deployment
   - Map release to IaaS
- Release
   - package with some jobs
- Stem cell
   - Base VM with BOSH agent

# Release
- Manifest
- Packages
   - Spec
   - Packaged bits
- Jobs (This includes stuff like monitoring for the service)
   - Spec
   - Monit
   - Template

# Deployments
- Take a bunch of releases
- Make compilation VMs.
- Canary settings.
- Network configuration.
- Resource pools (VMs, disks, networks)
- Jobs.
- Job properties.

# But how?
- "not all software was designed to be managed."

# Rant
- Don't automate brokeness.
- Don't just automate what you do right now; try and revisit why.

# Pareto power laws

# Warning
- This is not for deploying a single instance of wordpress.
- Learning curve: _|
