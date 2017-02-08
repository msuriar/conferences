# Configuration management is a solved problem

- John Vincent

## 2011
- "CM is a solved problem!"
  - Not quite. The tools do what they said they'd do.
  - Not everything fits the CM model.
  - Past behaviour is no indicator of future performance.

## 2017
- People here.
  - Services matter, not servers.
  - But we still have servers.

## What are we still missing?
- What does a "next gen" CM look like?
- Active Enforcment
  - configuration drift and next gen CM
- [question] What about canaries?
  - Don't know.
- [question] People messing with machines under CM is a people problem?
  - No. (Although valid use case.)
  - We rely on our configuration management tool to configure things the way we
    consider to be secure.
  - If any of that changes, we are "insecure" for some definition of secure.
  - e.g.adding/removing users.

## Currently
- CM is running
  - CM changes stuff
- CM not running
- Stuff changes underneath you.

## What if...
- We reacted to events indicating divergences from intent?
- We prevented changes which diverge from intent?
- But we don't have a good implementation.
    - inotify will fall over if we try and manage everything.
    - libnetfilter-queue analog?

## Distributed CM... ?
- Central CM server as a SPOF
- What if nodes could pull in state from a peer ring, instead of a central
  server?
  - Habitat supervisor.
- If you got that working, would you still need a central authority.
- [question] Any benefit to it?
  - It was cool?
  - I like the idea of stuff that fixes itself.

- [question] Tight definition of CM. How do you see integration between core
  configuration management and ancillary tools?
  - e.g. Jenkins for deployment?
  - I think we've abused CM, because we use it too much.
  - I've scaled back.

- [question] Different tools for other functions - do you mean other tools, or
  just another layer of config management?
  - Different tools.
  - Although, possibl
  - e.g. systemd didn't need a resolver, which is the counter argument.


