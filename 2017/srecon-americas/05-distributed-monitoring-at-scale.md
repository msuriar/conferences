# A practical guide to monitoring and alerting with timeseries at scale

## Monitoring sucks
- Because maintenance is expensive

## Nagios part of your complete ecosystem
- Check and test is insufficient.

## Ops sucks because
- Cost of something in ops needs to grow sublinearly with the growth of the
  service

## Principles
- Spends < 50% of time on "ops work"
- Make it go away.
- What is "monitoring"?
  - incident response
  - performance analysis
  - capacity planning
  - failure detection

## Focus on failure detection
- Alert when the beer supply is low.
  - Supply - 1 -1 == 1 ==> ALERT(TooFewBeer)
- Some alerts don't map to a simple threshold.
  - How long do we need to respond to the page?
    - Calculus, yay!

## Alerting on rates of change
- Speed clip.

## Distributions
- Quantised histograms and percentiles after the fact are very annoying.

## Alert design
- Monitoring can suck if you create too many alerts.

## SL[IOA]s
- Clients will provision against your SLO.

### Error budget
- The SLO is as good as your clients need, but not better.
- The SLO is also as bad as necessary to prevent humans being overloaded.
- Allowing the service some room to fail to experiment with features.

## Philosophy on alerting
- Urgent.
- Actionable.
- Require intelligence.

## Alerts don't have to *page*
- Diagnostics on a console.
- Low priority tickets
- Entire talk is assumed your service is engineered to survive single component
  failures.

## Prometheus architecture
- Target job
- Prometheus scraper
- Web browser.
- Alert manager
- Scraping shards
- Global aggregators.

## Recap
- Use "higher level abstractions" to reduce cost of maintenance.
- Use metrics, not checks, to get Big Data.
- Design alerts based on Service Objectives.

## Questions
- SLO violation based alerting leaves it too late.
