# How I learned to stop worrying and love the container

- Paul Bellamy
- @pyrhho

## Weaveworks
- Open source container management.

## Journey to architechture
- Sucking at something is the first step towards being sorta-good of something.


### Pets
- Terrible.
- Migrate from lots of special casing to multiple backend stacks running the
  same code (different config) but route to them based on nginx/frontend proxy
  config.

### Typos
- Eternal vigilance is not a good plan.
- Make safe tools.
- Safe tools shouldn't really be complicated.
- Safe tools are simple tools.


### DoS-ing Dockerhub
- No metrics for this, because we wanted the feature first.
- Fix with metrics
- "When you can measure  what you're blah blah" --Kelvin
- What gets measured get managed.
- Focus on
  - Rate
  - errors
  - duration
- Utilisation, saturation, errors solve a different problem.
- Alerts. How do you design good alerts
  - Alert on symptoms, not on causes.
    - Causes come from dashboards.
  - Alerts should be consistent across all services.
    - Lowers cognitive load.
  - Alerts should be actionable.
    - If you get an alert it should mean the person oncall has to do something.
- grafanalib - Python DSL for managing dashboards
- MTTR > MTBF

### Version diff alert
