# Self-Assembling, Self-Healing Architecture in AWS
- (mostly with HashiCorp tools)
- @jen20 - James Nugent

## Lots of products
- Focusing primarily on Packer and Terraform.

## Topics
- Zero provisioner.
- We hate provisioning. Shouldn't have more provisioning code than application
  code.
- Composition root pattern for multi-environment Terraform
- Self-assembly and healing.
- Packaging.
  - Just using Debian packages. Not really using containers.
- Bootstrapping "secret zero"
- Scratch-built AMIs with ZFS root filesystem.

## Thoughts
- Raw secrets in config files. Interesting.
- Weird thing where they use AWS autoscaling group API to modify their consul
  config.
    - Should be safe, I think?
- Signed instance metadata server token.
  - curl http://169.254.169.254/somethingsomethingsomething
- Oops, host key changed
  - rm .ssh/known_hosts fixed!
