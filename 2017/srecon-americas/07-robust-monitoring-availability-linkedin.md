# How robust monitoring powers high availability at Linked In

## LinkedIn 2016
- 107M active users, 467M total.
- 40 million messaging conversations per week.

## Feed architecture
- Business logic generates events, stores it, sends it to kafka
- Kafka is async.
- Read path generates topK events for each entity.

## Monitoring
- Load avg
- Errors
- Saturation
- Latency
- Instances

### How do we monitor?
- Mostly uses an internal toolset.
- Ingraphs. Frontend to rrd.
- Autometrics. Self-service metrics collections.
- Nurse. Autoremediation.
- Iris. Like pager duty.

## High avaliabiliyty.
- Data partition. (720)
- Replicas. (3)
- Backup and restore (separate backup nodes)
- Quotas (throttling etc)
- Failover (live load tests, etc. See previous talks)

## Best practices
- Automated hardware issue detection.
- A/B testing
- Proof rules (a.k.a. Error budgeting)
- Canaries
- Dark canaries

## Dark canaries
- When you have a bad canary, members are already impacted.
- Dark canaries: tee traffic from the production node to a canary node, and
  don't send the responses back to the users.
- This is interesting.

### For the feed
- Read only requests
- Scalability using traffic multipliers
- Dark canary failures have no impact on production.
- Differentiation from prod traffic
  - Page key: dark canary requests have separate page keys.
  - Tree id: separate tree ID.

### Dark canary usage
- New build verification.
  - Detection of schema changes, code issues, misconfigurations.
- New colo certification
  - How do you know if the new cluster is ready?
- Warming up caches in a multi colo environment.
- Capacity planning; set a multiplier, see how high you can go.

### Redliner
- Use live traffic in producton
- No special code
- No impact on prod, because dark canary.

## Advantages/limitations.
- Only works on readonly
- Watch downstream capacity
- Additional hardware.

## Questions
