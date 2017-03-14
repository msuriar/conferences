# Real time infrastructure
- Sharing pictures of kids
- (Goats)
- Likes and typing are realtime.
  - Powered by an ephemeral pub-sub store.

## Pub-sub
- Millions of publishes per minute, billions of subscriptions.

## API
- Subscribe(string topic, callback handler)
- Publish(string topic, string payload)
- Unsubscribe(topic)
- Subscriptions are ephemeral; tied to the lifetime of the connection.

## Internal goals 2016
- Understand reliability.
  - Didn't have introspection.
- "Billion or bust"
  - 1 billion people should be able to look at the same post and we don't care.

## Arch
- Device <--> Gateway
- Gateway --> Subscription Store
- Subscription Store --> Routing
- Routing --> Gateway

## Understanding reliability
### Mistakes
- The network is the only source of problems.

## Step back
- Define reliability
- R = deliveries / subs.publishes
- How do I get the number of subscribers?
  - Difficult. Ephemeral state.

## Durability
- Subscription store was single instance.
- Replicate!


## Thundering herd
- d(subscribers(topic))/dt
- 1E9 storage entries.

## Stepping back in
- Terabyte per publish.
- Rearchitect, rethink roles
- Routing, sub-store, gateway.
- Routing + sub-store, endpoint store (gateways, topics).

## Goals
- Understand reliability
- All the counts are computable on a single host.

### Reliability rethought
- Gateways reached / Gateways subscribed
- Path reliability from routing to gateways.

### Billion or bust
- Simple load balancer, spin up more gateways, fine.
- All of this is testable.
- Test endpoint store can fan out to all gateways
- Gateways can replicate to all endpoints.

## Lessons learned.
- Take a step back
- Aim high; use big numbers
