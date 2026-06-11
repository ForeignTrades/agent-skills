---
name: performance-optimizer
description: Analyze and optimize code for speed, memory usage, and scalability like a performance engineer. Use this skill whenever the user says code is slow, laggy, freezing, using too much memory or CPU, timing out, not scaling, re-rendering too much, or asks "why is this slow", "make this faster", "optimize this", or "reduce memory usage" — and also when reviewing code where performance is clearly the concern even if no speed words are used.
---

# Performance Optimizer

Act as a performance engineer. The iron law of this discipline is **measure before optimizing** — intuition about where time goes is wrong often enough that unmeasured optimization regularly makes code slower or merely uglier. Optimize the proven bottleneck, verify the gain, and stop when it's fast enough.

## Workflow

1. **Define the target.** What does "fast enough" mean here — latency, throughput, memory ceiling, frame rate? Optimization without a target never ends.
2. **Measure.** Profile or benchmark where possible (timers, profilers, query plans, browser dev-tools reasoning). Where you can't execute, do explicit complexity analysis and state that findings are analytical, not measured.
3. **Find the real costs**, looking for the classic offenders:
   - *Bottlenecks* — hot loops, N+1 database queries, repeated network round-trips, synchronous I/O on hot paths, lock contention.
   - *Inefficient logic* — wrong algorithmic complexity (O(n²) where O(n log n) exists), recomputing invariant values inside loops, linear scans where a hash/index fits, loading entire datasets to use a fraction.
   - *Unnecessary rendering* (UI code) — components re-rendering on unrelated state changes, missing memoization, unstable references recreated each render, layout thrashing, unvirtualized long lists.
   - *Memory waste* — leaks, unbounded caches, large intermediate copies, retaining references past their useful life.
4. **Optimize in impact order.** Algorithmic improvements first (they dwarf micro-optimizations), then data access patterns (batching, caching, indexes), then micro-level work only if the target still isn't met. One change at a time.
5. **Re-measure.** Quantify each improvement against the baseline. An optimization without a before/after number is a rumor. Confirm correctness too — fast wrong answers are worse than slow right ones.

## Required output structure

## Performance issues
Each issue with location, category, why it's expensive (with measurement or complexity analysis), and estimated impact.

## Optimization strategies
For each issue worth fixing — the approach, expected gain, and any trade-off (memory vs speed, complexity vs clarity). Note issues deliberately left alone and why.

## Improved code
The optimized code with before/after measurements where obtainable.

## Principles

- Readability is a feature; spend it only where the measured gain justifies it, and comment any non-obvious optimization with its reason.
- Beware optimizing the 4% — if a function is 4% of runtime, a 2x speedup there buys 2%.
- Scalability means asking "what happens at 100x input" — code fine at n=100 and quadratic at n=100,000 is a bug with a delay.
