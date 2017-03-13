# Automated debugging of bad deployments

## Bad deploy
- Bad code being deployed, success rate drops.
- Where is the bad code?
- Many commits per deploy.
- Many deploys per day.
- Resoltion.

## Bad deploy: resolution
- Roll back
- Debug
  - Identify bad commit.
- Fix problem
- Move on.

## Types of errors
- Performance regressions.
- Broken web pages
- Empty results
- Unexpected status codes.
- ...
- Stack traces
  - Very common, lots of intermation to help triangulation.

- Find new stack traces
  - Dedupe etc

- Finding the bad commit
  - In: stack trace, range of commits
  - Out: commit that broke.

## Finding stack traces
- Log aggregation
- Prioritise real time vs completeness.
- Use ELK.

## Old vs new
- Too many traces to inspect manually.
- Elasticsearch REST API.
- Compare two queries.
  - Canary vs production
  - Before and after deploy

## Deduplicating similar stack trace
- Simple string matching doesn't work.
  - Line numbers.
  - Different code paths.
- Filter and aggregation query in elastic search.
  - Aggregate by:
    - Exception name (TypeError)
    - File name (test.py)
    - Exception value (unsupported operand types for +; 'int' and 'NoneType')
      - Exception values may contain variable values.
      - Too many exception values in a file, probably a variable in the
        exception name.

## Finding bad commit
- Manually?
- git blame?
- git whatchanged?
- ...

## git-stacktrace
- https://github.com/pinterest/git-stacktrace
  - Files touched in commit shows in stack trace.
  - Line of code from the commit shows up in the stack trace.
  - Commit caused a different code path to be executed which in turn returned
    stack trace.
- Tradeoff - too many vs no matches.
- Idea: 5 commits are easier to review than 71.
- Ranked list of all possibly related commits.

## Implementation
- git log --raw # files touched in the commit in stacktrace.
- git log --patch # stack trace line numbers with lines chaned in commit.
  - Breaks if a later commit adds/removes lines in the file.
- git log -S # commit added a line of code in the stack trace.
  - git pickaxe ?

## Uses at pinterest
- Ron on every API and web deploy
- Allows us to quickly detect new rare errors.
- Significantly reduced debugging time.

## Questions
- Elasticsearch: are the queries built in to git-stacktrace?
  - Separate. Elasticsearch queries are customised.
- Metrics on what percentage of errors/incidents this has helped with?
  - No hard numbers, but paid for itself.
  - We see this multiple times in the deploy.
- What does the workflow look like once you've found a commit?
  - Manual process.
  - Ask the author. Failing that, ask reviewers.
  - Depends on the impact. 500s on homepage is a Bad Thing.
