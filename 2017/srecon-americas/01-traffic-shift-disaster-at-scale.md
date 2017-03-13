# Traffic shift - avoiding disaster at scale

## Production SRE at LinkedIn
- Assist in restoring stability during site critical issues.

## Terminology
- Fabric/colo - linkedin datacenter with the full appliaction stack deployed.
- Pop/Edge - entry point to linkedin. (TCP/SSL termination)
- Load test - planned stress testing.

## Linkedin infrastructure evolution.
- Launched 2003
- Until 2010, single colo in the south bay.
- 2010, Linked In datacenter. (No redundancy)
- 2011, DC2, active backup.
- 2013, active-active
- 2014, multi-colo, 3-way-active
- 2015, 4 datacenters, active active.

## 2017
- 4 DCs
- 13 PoPs
- 1000+ API endpoints.

## What are disasters?
- Service degradation.
- Infrastructure issues.
- Human error.
- Datacenter on fire.

## One solution for all disasters
- Traffic shift.
- Reroute user traffic to different datacentres without any user interruption.

## Flow
- Border router
- IPVS # what is this?
- Apache Traffic Server (Stickyrouting services - main magic)

## ATS
- Looks at request header. Crytographically signed cookie, includes target DC.
- If cookie is invalid, asks stickyrouting service for primary DC for a user.

## Stickyrouting
- Datacenter is a location.
  - Each DC split into 100 logical buckets.
- Every bucket is either on or off.
- If {DC,bucket} in a DC for a user is off, reroute.
- Offline map reduce to a primary/backup datacenter to each user.

## Advantages
- Less latency for users.
- Store data only where it's necessary.
- Provides precise control over capacity assignment.

## When to TrafficShift?
- Daily, twice a day.
- Impact mitigation.
- Planned maintenance.
- Stress testing.

## Site traffic, disaster recovery
- Plan for two datacenters to go down at any one point.

## Traffic shift architecture
- Web application.
- Couchbase
- Backend worker processes.
- Use Salt to push stickyrouting config.

## Load testing
- 3 times a week.
- Peak hour traffic.
- During peak time traffic.
- Fixed SLA; if alerting fires, stress test ends.

## Benefits
- Capacity planning.
- Production traffic - see load for real query mix.
  - Service owners look at data to see how their service performed.
- Identifying bugs in prod
- Confidence in disaster recovery.

## Big red button
- Kill switch.
- Fail out of a datacenter/PoP in less than 10 minutes.
- Minimal user impact.

## Takeaways
- Design infrastructure to facilitate disaster recovery.
- Stress test regularly to avoid surprises.
- Automate everything to reduce MTTM.

## Questions
- Stickysession: do you have two versions of stickysession?
  - We have DC to DC traffic for replication, not for online APIs.
  - Stickyrouting is only for externally sourced traffic.
- How do you handle replication?
  - We expect it all to be real time.
  - Replication falling behind is a failure.
- For automated traffic shifting, how do you avoid flapping?
  - During stress testing... something.
- Is a bucket an absolute unit of capacity, or is it a ratio compared to the
  location?
  - All US locations are basically the same.
