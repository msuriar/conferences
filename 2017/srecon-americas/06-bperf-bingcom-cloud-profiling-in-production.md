# BPerf - Bing.com Cloud Profiling in Production
- Frontend stack performance
- Developer platform team for making using it easier.

## Agenda
- bing.com frontend int
- What
- Why
- Bing
- Bperf
- Walkthrough
- Case study

## bing.com frontend
- C# ASP.NET MVC on Win2016
- Entry point for all traffic after Azure CDN
- Rendering layer. Razor --> HTML.
- "Backend": set of microservices talking to indices.

## more intro
- Query mix {olympics 2016, katy perry, coreclr}
- Release velocity - multiple times a day.
- Feature velocity - 100 commits a day
- Experimentation - Hundreds of A/B testing "flights".
  - Combinatorial explosion.
- Summary - there is no "canonical workload"

## What is profiling in production?
- Identifying/isolating lines or regions of code which cause (directly or
  indirectly) unusual application behaviour.
- Direct: developer code.
- Indirect; library call, syscall
- Should not perturb the profiled application.
- Often platform specific tools. (dtrace, etc)
- Not a replacement for higher level tools

## What is profiling in production?
- Identification ==> High level (aggregate metrics)
  - aggregate metrics by dimension
  - Developer instrumented code markers
- Understanding ==> Low level (memory, CPU profiling, code recompilation for
  telemetry.)

## Why profile in production?
- High level tools great at identifying traffic.
- Some great at mitigation as well
- PIP useful wwhen you can't mitigate
  - e.g. query of death
- Deep understanding without a debugger.
- Helps with root cause analysis at time of incident.

## bing.com and profiling in prod
- 4 years ago at 0300.
- User query and a feature flag had a non-obvious infinite loop.
  - Multiple loop control variables.
- Every time query hit a machine, lost a CPU core.
- Debugging: Finding and understanding the code
  - Finding code involved binary searching through log entries.
  - Understanding required building code in a standalone app.
- "How do you find an infinite loop in your application?"

## bing.com and profiling in prod
- What would have been great?
  - CPU profile (what's hot on the CPU)
  - Ability to inspect local variables and parameters.

## Introducing bperf
- Event Tracing for Windows (perf, dtrace)
- Always on CPU sampling profiler
- Periodically triggered memory sampling profiler
- Disk, network I/O.
- .NET information (gc, exceptions, JIT)

## Introducing bperf
- Practical only when high level analysis points to code.
- Machine, time interval.
- Hopefully offending code has been caught in action.

## BPerf CPU sampling profiler
- Collects a callstack "sample" every 10 milliseconds on all logical cores
  - 100 usec pause every 10ms.
- Correlate with search request or background operation.
- Aggregated at the datacenter level.
  - "How much time are we spending in string processing?"
- Canonicalisation (instruction pointer ==> friendly name) happens on the
  machine for JITted code, off box for native code.

## BPerf periodic memory sampler
- Trickier to sample memory as allocators hide effective usage.
- Managed memory is sampled every 100KB of allocations.

## BPerf disk/network
- Disk accesses on the request thread are logged.
  - Checked against whitelist of allowed files.
- Standard instrumentation of network information

## BPerf -NET
- GC events.
  - Search query impacted by GC is marked specially.
- JIT compilation events
- Exceptions
  - Global rate is tracked, and each call stack is logged.
  - Also identifies cases where developer catches and swallows exceptions.

## BPerf - recompilation
- Modify running code at the method level without impacting the service.
- e.g logging parameters, local variables.
- Fix simple bugs without a redeployment.
  - try/catch for nullref.
- Complex fixes: trampoline to redirect to new method.

