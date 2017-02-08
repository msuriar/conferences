# Troubleshooting Kubernetes
- Jorge Salamero Sanz
- @bencerillo

## How we used to do performance troubleshooting?
- uptime
- free -m
- ps aux
- vmstat 1
- netstat
- strace

## Now
- Things are complicated.
- namespaces, cgroups, etc
- Troubleshooting inside containers is a pain.


## Sysdig
- Opensource troubleshooting tool, swiss army knife.
- Why not EBPF?
  - It wasn't enough to do everything we wanted.
  - No it's more stable and more complete.
  - But so far this kernel module has worked very well for us.

## Service orientation
- Capture system events, filter, run scripts
- Trace dumps
- Capture analysis
- CLI or ncurses interfaces

## Demo

## Impressions
- Pretty cool. Would be nice to not need another kernel module.
