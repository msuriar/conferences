# Quick reliable deployments

## How many times does Uber deploy per day?
- Good question.

## Past
- Monoliths
- Path to production (Dispatch service)
  - Small city 2hours
  - Medium city 3 hours
  - Large city overnight
  - All cities with < 10 trips
  - < 100 trips
  - < 1000 trips
  - Global
- Very manual, very slow.
- More people we've hired, the slower it got.
- Deployment schedule means that people would sneak things in at the last
  minute.

## Today
- Thousands of microservices at Uber.
- Deployment is automated. Things are faster and better.

## However
- Move to micro services ==> move to all active.
- We still noticed errors/reliability problems.
- 2015 --> SRE at Uber.
- First thing we did was detect,mitigate,root cause outages.
- 80% of outages caused by code deployments.
  - Deployment without guardrails.

## Define set of release principles
- Automated canary for every service.
- Staged rollout.
- Few zones.
- Degradation + step pattern makes it easier to reason about outages.
- Every service roll out in the same order.
  - Can't know which services are rolling out at any given time.
- Self service canarying/rollback metrics.
  - Error rate.
  - Business metrics. (Unfulfilled; drivers going offline, etc)
- Workflows for common cases.
- Observation: single rollout framework for everyone.
- Have breakglass if you need to roll forward quickly.
  - Question: allow fast rollback?

## Results
- Lower TTM
- Reduced incident scope.
- Less time in incident review.

## Takeaways

### Fast detection isn't always easy
- Detecting error rate is easy.
- Drivers, ETAs, surging, etc.
  - Lots of this changes due to local events in cities.
  - Not easy to detect.

### No one likes slowing down
- Many engineers were manually doing something similar.
- When you do this centrally, people take it as a lack of trust.
- No one likes slowing down, including SRE.

### Plan for reliability at the start
- We should have put in the guardrails for microservices at the start.
- Going from zero controls to some controls is difficult.

### Policies driven by metrics are easy to promote
- Once we have data, we can build a case for why it should take an hour, or 45
  minutes, or whatever. Because we know what our MTTD is. etc.

### Velocity/reliability tradeoff is a moving target
- Bias towards velocity (without compromising safety)

### Reinforce failure domains everywhere
- Other systems around the company started to take failure domains as the unit
  of rollout onboard.

## Questions
- What tooling did you use to get data?
  - Proprietary TSDB.

- TTR/TTD?
  - Track incidents in "The Commander"
  - Manual review.
  - Anything that took out a city or more, does a deep dive.

- Deploys - include config?
  - Service config using the same system.
  - Others that use different things. Dynamic config, faster.
- Client rollouts?
  - more stringent.
  - feature flags etc.

- Rollout/rollback?
  - Policies defined in YAML. Normal rollout, fast rollout, fast rollback, etc.
