# Monitoring and config management
## Survey on monitoring
- Interesting.
- Confirmation bias; survey from hipsters.
- 9% of developers do any monitoring.
- Most people monitor the wrong things.
   - We monitor system metrics, not service metrics.
- 90% have unmonitored failures.
- 80% have unactioned alerts.
- 33% monitor reactively. (Only put in checks when something broke.)

## Tools don't scale
- Centralised, monolithic systems need to vertically scale. This sucks.
- Things need to be self-service.

## Why?
- Horses hate talking about unicorns.
   - How can I convince a dev to include metrics?
   - Learned helplessness.
   - A few unicorns do not make horses magic.
- Change is slow.
- People don't know about new stuff.
   - e.g. Puppet changing a root password not believed by a mid-Western
     company.

## Finance
- ROI on monitoring investment is not obvious.
- Investment is expensive.
- Lots of unknowns in terms of what's hooked in to your monitoring system.

## There is hope!
- Config management as default.
- 73% of respondents to survey use config management in some form.
- "Blessed are the toolmakers" - change software to make it easier to monitor.

## Suggestions
- Generate events instead of log files
   - Realtime
   - Consumable
   - Responsive
   - Composable
- APIs and endpoints
   - Queryability, introspection.
- Create monitoring abstractions
  - e.g. check types with providers for multiple monitoring systems.
- Build monitoring patterns into content.
- Set quality bar to include monitoring.
- Testing complements monitoring.
- Service discovery and registration first class citizens.
   - zookeeper, etcd, consul
- Enable self service
   - Focus on more than just the operator.
   - e.g. enable developers to configure their own monitoring
