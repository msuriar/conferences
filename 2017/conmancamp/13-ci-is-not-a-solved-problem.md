# CI is not a solved problem

## Why?

### Bad assumptions
- Assume you're building software
- Assume you're producing an artifact
- Known set of languages
- Build process is well defined

### Not good for "non-traditional" software
- CM/Infra-as-code
- Network configuration
- Database schemas
- (comment: configuration is code. If it's in version control, then it is all
  code.)

## Tried jenkins
- OMG it was terrible.
  - Well, not really, but it definitely worked for me.
  - https://cyclid.io/

## Ideally
- Unopinionated
  - No specific workflow or toolset
- Agnostic
  - OS, cloud platform, language
- Flexible
  - ... functional requirements change
- Operable
  - Needs to be easy to install and manage with config management tools

## Comparison
- Jenkins
- Travis
- CircleCI
- Codeship
- Concourse
- ...

## Cyclid
- Ruby, rest API
  - Well understood, boring, easy to manage.
  - First class plugins
- Everything is a plugin.
  - Keep things highly decoupled where they're not.
- Keep component & dependency footprint as small as possible.
  - Reverse proxy, Cyclid, Redis (local queue), "an SQL database'

## Everything is a plugin
- Builder
  - Create build instances
  - No builder for AWS because author hates it.
- Transport
  - Communicate with instances
- Provisioner
  - Configure instances
- Action
- Source
- API
- Dispatcher

## Config
- JSON or YAML
- "stages" have baked in versions.
- Environments
  - os
  - package repos
- Sources
- Secrets
  - tokens, passwords, keys
- Stages can also be defined on the server.

## What does the future look like?
- What have we learned from config management?
  - Flexibility is good.
  - It's fine to have more than one tool.
    - Competition is good.
  - Different tools and workflows suit different users.
  - Composability is good.
  - Data driven is good
    - DRY

### Composable CI
- Every CI job is a snowflake
- Cyclid is built with Composability in mind
  - Every job and stage is versioned
  - Stages can be defined on the server and used across different jobs.
- Next; sharable stages
  - We've done it with config management
  - Just another API
  - ... but needs dependency management.

### Data driven
- Required because of composability
- What would it look like?
  - What data sources?
  - Organisation?
  - Expose to jobs, users?
- Jenkins is the closest, with parameterised builds.
  - Limited scope
- Start the conversation.

### Logic
- Let's stop pretending CI jobs don't require logic
  - Stop externalising into shell scripts
- only_if/not_if
  - Same as conditionals on resources in config management.

### Event framework
- Simple state machine
- Events emitted during a job consumed by plugins
  - Fan out, fan in
  - Notifications, chains
  - Deep job introspection ad profiling
  - Monitoring & statistics

### More?
- More plugins?
  - AWS builder
  - Redhat provisioner
  - !Linux
  - Deployment
- Docker
- Vagrant
- Qemu
