# Breaking things on purpose with Gremlin

## Who am I?
- Failure testing at Amazon.
- Netflix
  - ChaosMonkey etc
  - LatencyMonkey
  - FIS; failure injection service.
    - Impact individual request.

## Context not control
- Netflix core value
- What's the opposite of fragile?
  - Robust? NO!
  - Anti-fragile
    - Bounded downside, unbounded (or at least larger) upside.

## Immunity
- Inject something harmful in a system in order to build an immunity

## Simple testing can prevent most critical failures

## Effective failure testing
- https://github.com/Netflix/Hystrix
- Think about failure testing from a threat model perspective.

### How likely is this to occur?
- Repeated previous examples you should fix.
- But what about unknown unknowns.
- What is the cost of being wrong?

### Quantify value you're providing to the business?
- Difference between three 9s and four 9s.

## Validating assumptions

### Experiments
- Hypothesis
  - Lose rating service, get default ratings.
- Measurable outcome
  - Increased Hysterix fallbacks
- Success criteria
  - Overall success rate remains constant.
- Abort conditions
  - Halt immediately if members are unable to stream.

### Communication
- Tell people when you break stuff.

### Think small to start with
- Start with the smallest possible impact that will teach us something.

### Then dial it up
- Functional testing is for small/single instance deployments.
- Prod level - resource constrains, queueing, cascading failure.
- Easy to tune for the happy case.
  - You want to tune for the really bad case.

## If you haven't tested it, it doesn't work
- To be ready, stuff has to be tested/prepared.
- "Productionalisation".
  - Does the alerting work?
  - Does the alert go somewhere useful?

## Picard management tip!
- Run crisis drills when all is well. A real calamity is not a good time for
  training.

## Case studies
- Spinnaker
  - Cloud independent deployment tool.
  - When it first came out, wasn't quite ready.
  - Consultation, whiteboard session.
  - Once people get used to a system, falling back to manual is harder.
- ChaosKong
  - Netflix traffic/chaos team.
  - AWS outage isolated to a region, Netflix evacuate that region.
  - Every couple of weeks, netflix evacuates one of those regions even if
    something's not broken.
- Three outages mitigated by ChaosKong
  - Sunday morning, EC2 not spinning up new instances.
    - Moved traffic to another region.

## What is Tier 1?
- Finding the critical services.
  - Amazon: What is tier 1?
  - Some PMs have a list of that services.
  - If you were on that list you got paged for major incidents.
- Netflix
  - List critical services.
  - Have an isolation test to make sure that new dependencies were added
    deliberately.

## Paper
- Automating Failure Testing Research at Internet Scale
  - Integration with distributed tracing infrastructure.
  - 10 requests an hour, we'd annotate traces with failures.

## Outcome
- Reduce toil
- Increase reliability
- Be prepared for outages that occur

## Questions
- What should small shops do?
  - Fail each dependency to start with.
- whiteboarding - don't trust people's memories
  - Tracing systems help.
- Have you seen anyone migrating from one service provider to another?
  - Not yet.
- Multi-cloud deployment using Spinnaker.
- Best case to do this is in production
  - Is there value in doing this in the development cycle?
