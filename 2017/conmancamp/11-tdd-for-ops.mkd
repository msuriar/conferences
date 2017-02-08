# TDD for ops
- 
- 

## Origins
- NASA.
- We need testing to be sure we are doing no harm.

## Process
- Create a test
- Make it pass
- Repeat.
- Only refactor while tests are green.
- Only merge when tests are green.

## Steps for ops
- Define a feature.
- Write some code.
- RSPec and ServerSpec.
- Go back and forth between tests and code.
- Run tests.

## RSpec/Serverspec
- No AMI created unless all the tests pass.
- http://serverspec.org
- Can also verify AWS resources.

## See also
- testinfra
