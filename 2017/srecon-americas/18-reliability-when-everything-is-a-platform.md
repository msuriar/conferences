# Reliability when everything is a platform

- Disclaimer: reliability != availability, but for this talk let's pretend they
  are.

## In the beginning...
- There is a product.
- Let's call it search.
- Build it.
- Launch it.
- Goes well, get users, get more users.
- Software systems are governed by network effects.

## This needs to stay up
- So... SRE.

## Entrepreneurs are pessimists who aren't good at maths.
- So they turn up a new thing. Call it mail.

## Humans hate inefficiency
- Engineer says search and mail both need storage.
- We should refactor.
- Pull out storage requirements into a "thing".

## But but but...
- This looks like an engineering problem, but...
- Before you refactored, you had users.
  - After you refactored, your applications are also users. Of your platfrom.
- Roles get squishy.

## Platform
- A system with an API

## Application
- A system with a UI

## Team mitosis
- Cognitive load.
  - Number of different pieces.
  - Different systems.
- Then you have to split.
  - Platform vs app
  - Frontend vs backend
  - Whatever you want to split.

## What's the next step?
- Applications are vulnerable to network effects
- APIs as far as the eye can see...

### Complication
- What happens when you provide a platform to someone outside your company?

## Principles
1. The most important feature of any system is its reliability.
  1. Nothing in nature is 100% reliable.
2. Our monitoring doesn't decide our reliability. Our users do.

## Problem
- The experience of the customer (person building an API at your platform).
- It's not constrained by the four corners of your job as an SRE.
- 99% on top of a %99.999 platform = 98.something.

### Counter 1
- "I'm good... My application doesn't have an API..."
  - "You may not have an official one."
- Pokemon Go.
  - After the initial few days... number one complaint - 3rd party scraping
    service is down.
- You have an API. Do you support it or not?
  - You have to.

### Counter 2
- Reliability is a solved problem?
  - Best practices
  - deployment guide
  - code snippets

## Principle 3
- 99.9% software
- 99.99% operations
- 99.999% business

## SRE math review
- 99.9% == 43.2m error budget

## Assertion
- Your platform can only get 99.99% by luck if you don't have integrated
  operations with your customers.

## And therefore...
- We need to SRE our customers.

## Stage 1
- Application readiness/reliability reviews.
- Inspect the application components which are 1) critical and 2) rely on your
  platform.
- *most* important thing you can do.

- Questions:

### What is your current reliability?
- Prove it.
- 1/3rd of the time measuring is not useful.
- SLOs not tied to business objectives.
- Which means platform provider gets rubbish support tickets.
- Key: alert on symptoms not causes.

### What are your SLOs/SLIs?
- Most customers have implicit (rather than explicit) SLOs that are only
  intuitively tied to their business objectives.
- If you don't have an SLO, your SLO is what your customers experience.
- Key: sane error budgets and ways to address misses.

## Stage 2
- Shared monitoring
- Common source of truth between teams.
- They only page on metrics in the shared monitoring, no secret data.
- Shared monitoring is everybody's bestest friend.
  - Can't do 99.99% without it.
  - Helps eliminate the blame game.
    - If all the data is in the shared monitoring, that's a great place to be.
- Blackbox probing is hard.
  - Mimic the things that users see.
  - Guess work, voodoo, expensive.
  - If you do this shared monitoring, you have actual customer data.

## Stage 3
- Operational rigour between teams.
- Every postmortem is a joint postmortem.
  - AIs assigned in both directions.
  - *YOU* own and drive the postmortem process. *YOU* are the incident
    commander.
    - Your lever to convince the customer to change things are the AIs in the
      postmortem.
- If a postmortem doesn't have at least one AI on both sides, that's a red
  flag.
    - We broke it, how could the app have been more resilient?
    - They broke it, can we make the platform better?

## Stage 4
- If you've got this far, you have a customer with a more reliable system.
- Joint oncall.
  - You are not running your customers systems, deploying their binaries.
  - When they spin up a warroom, someone from your side is joining.
  - Humans don't like talking to vacuums.
    - This turns a bad moment into a trust building exercise.
  - Regular DiRT, WoMs.
  - If your company permits it, joint projects.
    - Tooling development?
    - Documentation?
    - ???
- Train with your customers.
  - You can only fight the way you practise. (Musashi, B5R)

## CRE
- Group of Google SREs
  - Pointed outwards instead of inwards.
  - Comfortable talking to customers.
  - Software development (esp. externalising internal SRE tools)
  - ARRs (or making them easier)
  - Ongoing design review.
  - Build and maintain shared monitoring.
    - Customer contributes metrics/SLOs, but we build the monitoring.
    - For our teams to trust the data, "Google SREs built the system".

### So... professional services?
- No. You are not charging for this.
- Because... if you want to have the ability to provide support, you need the
  moral high ground. (Can't hand back the pager if they're paying us.)

## TL;DR
- Everything is a platform.
- Reliability is the most important feature.
- You need to SRE your customers.

## Questions
- dnb: where do you push back to?
  - Customer oncall team.
- How big of a customer do they need to be before you do this?
  - Process engineering. Headcount comes from the sales team.
    - Head of Sales does a stackrank.
    - Willingness veto. If the customer isn't willing, we don't engage.
  - How do we scale?
    - Qualified service partners.
    - Technology partnerships.
      - Vendors. e.g. Pivotal.
- Platforms building applications
- What happens if all these organisations have a CRE model?
  - Eventually working together is better than fighting eachother. Unsolved
    problem. We'd like to solve it.
- Need to SRE customers.
- Does that work the other way round? Do you need to SRE your 3rd party
  dependencies?
   - Yes.
