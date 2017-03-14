# Reducing MTTR and False Escalations - Event Correlation at LinkedIn

## False escalations
- Dependencies
- Misattribution

## Production SRE @ LinkedIn
- Reducing MTTD/MTTR
- Direction on site monitoring.
- Tooling for troubleshooting, detection, correlation.
- Assist in restoring stability to services during site critical issues.

## Problem statement
- Reliability goes down, learning curve/MTTR go up with service complexity.


### Technical goal
- Find a problem with a service between a given time period or ongoing using:
  - Unified API
  - Web Frontend

### Success criteria
- Reduce MTTR on incidents
- Reduce false/needless escalations
  - Our SREs and our engineers shouldn't be hassled. (SREs are engineers. >.<)

## Architecture options
- Real time metrics analytics
  - Fast
  - Advanced analytics in real-time
  - BUT resource intensive
- Ad hoc metrics analysis
  - Smaller resource footprint
  - BUT slow
- Alert correlation
  - Leverages existing alerts
  - Strong signal/noise ratio
  - BUT constrained to alerts only.

## Correlation engine overview
- Drilldown + site stabilizer
  - Near-Time metric analytics & event correlation
- Invisualize
  - Alert correlation.
- Existing knowledge available in both.

### Where to get started?
- Correlation is great.
- Need to understand dependencies.
- Built a callgraph!

### Callgraph
- LinkedIn applications emit metrics on a per-API and per-dependency basis
- Scrape metrics index
  - rest.li
  - voldemort
  - espresso
- Collect call count and latency.

### Drilldown
- Using call graph, identify "high value" dependencies.
  - Use call rate as a proxy for value.
- k-means unsupervised, 5m chunks, find similar trends.
- Queryable APIs
- Outputs correlation confidence scores.

### Invisualize
- Analyses alerts (in realtime) from each service.
- Callgraph to find the unhealthy service and affected services.
- Visualises it.

### Site stabilizer
- Collates recommendations from Drilldown and Invisualize.
- Decorates recommendations with
  - Scheduled changes.
  - Deployment events.
  - A/B experiment changes.

### Correlation-fe
- API for auto suppression, remediation.
- Visual exploration.

## Workflow
- Nurse (autoremediation) can be configured to forward alerts to dependent
  services.

## Early results
- Siteops have greater visibility
- Reducing MTTR
- Reducing false escalations

## Conclusion
- Understand what correlation approach makes sense for you.
- Understand your dependencies.
- Build, Integrate and benefit!

## Questions
- Question: How do you deal with fan in?
  - Handwave handwave we deal with it.
- Question: What if the suspect service is still within SLO?
  - Lower confidence score. (I'm not convinced.)
- Does the frontend service ever find out they would have been paged?
  -No, we do a review.
  - jaq: maybe there's a signal still useful for the frontend to improve
    resilience?
- NURSE?
  - Inhouse.
  - Lots of blogs etc about it.
  - Workflow engine, triggered off random inputs.
- How does MTTD come in to play with this?
- How do you build your confidence score?
