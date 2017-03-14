# Every Day is Monday in Operations

- 10 axioms for modern operations
- Uptime vs velocity
- Everyone loves war stories.

## Every Day is Monday in Operations
- Services are always up, and always changing.

### Betting Against the Odds
- 1% chance per day, per node running the affected software.
- "The odds are never in your favour".
- 700k nodes. 700 nodes per day. Oops.
- Saltstack
  - Used as part of deployment/remote execution/configuration.
- Three reports of deployment failures in early integration environments.
- User reports, unclassified.
- 50% of all deployments failing.
  - You can't roll back, because your deployment infrastructure is broken.
- Couldn't find it for 2 days.
- On the third day, we found something.
  - Tiny change made to legacy system called ULL.
  - Only job in life was to tar up python libraries and extract them on every
    machine in the fleet.
- Change was benign.
  - Kafka capacity increase.
  - They're getting hammered by I/O. Let's I/O nice the extractions.
  - Change pushed to the entire fleet.
  - Race condition. Rather than winning all the races, we were losing > 1/100.
- Hit specific machine
  - Then needed to extract over the live files.
  - Python will happily import partially written file.
  - Parent processes held corrupted module in memory.
- 1 system issue resolved
  - 233 engineering hours per day saved.
- Without a change set, you have a manhunt.
  - With a change set and good timestamps, you have a police lineup.

## Site up
- Service responding reasonably to a request.
- Features, quality, schedule - pick two.
- Site up - this isn't optional.

### Scaling strategy - retirement
- You don't scale past a decom.
- Great runbooks, but two missing pieces
  - DR plan.
  - Scaling strategy.
- "Before you go, what's the scaling strategy?"
  - "Retirement."
- You can't just decom source control.
- Meeting on the calendar for January.
- Vacation.
- Get back, staff meeting.
- Partner engineer had retired.
- Found no metrics or alerts.
- Set up "the Observer framework"
  - Observer + adapter
  - Standalone daemon
  - Observed and emitted metrics.
- 8 hours later...
  - SVN at linkedin had bimodal traffic.
  - 18-23% of traffic dropping at peak.
    - Complaints being hidden by support.
- Everything invested in making SVN stable to get 6 months of runway.
  - Current arch was active/passive, single node.
- 6 node cluster, 5 write through proxies.
- Only thing left to do is fail over to the backup and fail back again.
- Two days before new DR site was ready, primary storage failed on the R/W SVN
  master.
- Host unrecoverable.
- SVN HA couldn't accept writes.
- DR strategy invalid. No DR site.
- SVN came back online repo by repo.
- More change in those 2 months than in the entire previous history.

- Never give up.
- Only one way to go, forward.
- Assumed that we had all available resources to this problem.
  - In the middle of the firefight it's hard to step back.
  - Ask for help. You would have had more.

## Site up
- Refusing to accept site up as normal.
- Doing everything within your power to learn.

## What gets measured gets fixed
- If you can't measure, you don't know whether it needs fixing.

### TS3
- Every day, every incident.
- "The tools are terrible, I wrote my own."
- Massively long internal survey.
- 1-10 scores, plus free text.
  - Results came in: NPS = -46.
- Went back to GCN tracking data
  - MTD, MTR.
- This was around the time the site reliability dashboard.
  - Mined that data.
  - Good news: supported the human powered data source.
- 6 months out of previous 12 had an ongoing tools incident.
- TS3
  - Gather every oncall for internal tools teams.
  - 30 minutes every day.
  - Every site incident.
  - MTTD, MTTR.
  - Production review.
  - Success criteria: reduce user impact.
    - Make it easy for engineers to open incidents.
  - Not counting total GCNs, or specific classes of outages.

## You're only as good as your lieutenants
- There is an upper limit to how effective you can be as an individual

## Scale or fail
- Technical gatekeeper. High bar for craftsmanship etc.
- Four people, throughput of 1.5 engineers.
- How do you get a set of team members who all exceed me?
- "My job is to help LinkedIn win."
- Stopped being a gatekeeper.
- Give people the major ideas and let them run with it.

## Don't assume anything
- LinkedIn is throttling.
  - What does it mean?
  - Dropping some percentage of user traffic to save the rest.
  - All frontends, so network was suspected.
  - Use short words and short sentences.
  - I'm going to ask simple questions and I will find cause.
    - We have no capacity problems.
      - Correct.
    - 4GB. 1x4?
      - 4x1
    - What's the utilisation on each of them?
      - Oops, one pinned.

### you're going to make assumptions
- Find the assumptions people are relying on in your current conversation.
- everydayismondayinoperations.com
