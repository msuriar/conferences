# Infrastructure as code
- @kief

## Speed
- Goal is velocity
- Ops seen as an impediment

## Risk
- There are things that we're trying to achieve that are important.
- Myth: velocity and doing things correctly are not at odds.
- State of the devops report.

## Rapid and responsible
- Move quickly and make small, fast changes.
- Places with lots of process sucks.
- Because their infrastructure sucks.

## Infrastructure as code
- Applying tools and practices from software engineering and applying them to
  infrastructure.

## Dynamic infrastructure platforms
- Compute
- Networking
- Storage
- Not just cloud; can do this on bare metal too.
- Programmable, on-demand ==> API

## Cloud and automation is amazing
- But then server sprawl
- Configuration drift

## Automation fear cycle
- Inconsistent servers ==> running automation will break stuff ==> make manual
  changes ==> ${1} ...

## Automation lag
- The longer it's been since running an automated process has run in the same
  context the more work is needed to run it again.

## Apply small changes frequently
- ... rather than large batches infrequently.
- ( comment ) Small batch sizes, see The Goal

## Continuously synchronise
- ... or continuously rebuild.

## DevOps
- How can we avoid damage from automated mistakes?
- War story: pushing /etc/hosts as a work around for DNS.

## Automatically test every change
- (comment) assumes that you have 100% test coverage.
- This is basic CI. Automated tests for your infrastructure.

## One definition, multiple environments
- This gets complicated, easy to screw up and push the wrong thing to the wrong
  environment.
- Probably one templated config, promoted from one environment to another.

## Tests are slow
- Organise into separate testable pieces.
- Test components individually
- Cumulatively integrate and test components together

## Designing for change
- Split infrastructure according to the scope of typical changes.
- Limit blast radius
- Loose coupling
- Try and avoid handoff between teams for common pieces of work.

## Where to split?
- Architectural? Frontend, backend, database?
- Lots of changes span teams.
- Mean you need to spin up project teams.
- Split things up to bundle things that change together.

Cycle time
- Measure and optimize elapsed time from identifying a need to satisfying it.
- Rebuild (Recover)
- New environment
- Update existing environments
- Introducing a new tech stack.

