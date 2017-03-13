# So you want to be a wizard

## Skill: Why is it important to understand your systems?
- Understand jargon.
- Helps you to debug really hard problems.
- Innovate.

### Skill: How do you learn?
- Learn fundamental concepts
- Recurse center (12 week programming retreat, NYC)

### Homework
- Build a really bad TCP stack from scratch.
- In Python.

### Experiments
- Deliberately OOM the system.

### Books
- Networking for System Administrators; Michael Lucas
- Linux Kernel Development, Robert Love
  - Read things that are too hard.

### Work with stuff in your job
- Do basic tasks with infrastructure.

### When you don't understand something, dig in
- Understanding the Linux Virtual memory manager

### It'll take a long time
- Learn to program in 10 years


## Skill: Ask great questions
- Start with saying what you know.
  - Helps organise thoughts.
  - Reveals misunderstandings.
  - Helps level set the answer.

### Don't ask the most experienced person
- Just ask someone with moderately more experience than you.
  - Less load on experienced people.
  - Lower bus factor
  - Improve knowledge.

### Do research
- Read stuff first, then ask the question.

### Ask yes/no questions
- e.g. does $DATABASE do hash joins?

### How did you do that?
- Ask people just when they've e.g. fixed stuff.

### Ask questions in public
- Particular more senior people.
  - More comfortable showing lack of knowledge.

## Skill: Read the code
- Understanding mystery error messages.
- No docs, no problem.
- Even hard codebases are possible to read sometimes.

## Debugging like a wizard
- 40ms delay between request and response
- Happened on the same machine.
- Client would send headers, then 40ms, then send rest of request.
  - Client was doing stupid stuff.
- Delayed ACK + Nagle.

### How do you get better at debugging?
- Computers are not magic.
- Impossible... but it happened. Why?
- Be confident that you can fix the job.
- Spend time fixing things that annoy you.
  - 1000 records/second isn't a lot. How do you know what a lot is?

### Train your intuitions
- computers-are-fast.github.io

### Know your debugging toolkit
- Linux debugging tools Zine.

### Learn to like debugging
- I don't understand what's happening/I'm going to learn something new. That's
  the best.

## Skill: write down a design
- Design small projects.

### Write announcement email first.
- Why is this important?
- How does it impact other teams?
- How do we know it's working?

### Write a premortem
- Imagine the project failed. Why?

### Track Changes
- Yes. This is normal.

## Understand the big picture
- "Why am I doing this?!"
- Approach project planning with excitement and curiousity.
  - Figure out why it's important.
  - If it's not, do something else.
- Leads to better technical decisions.
- Working on projects people care about is AWESOME

## Now we're wizards
- Understand systems
- Ask great questions
- Read the code
- Debug like a wizard
- Write down a design
- Understand the big picture.
