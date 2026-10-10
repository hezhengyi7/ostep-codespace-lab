## Q1
- Prediction：State table: 5 instructions, all CPU bound, no I/O. Total time = 5 ticks, utilization = 100%.
- Reasoning：The program only uses CPU, no waiting for I/O, so CPU is fully occupied.

## Q2
- Prediction：State table: 5 instructions, each instruction followed by I/O. Each instruction takes 1 tick, I/O takes 1 tick. Total time = 10 ticks, utilization = 50%.
- Reasoning：CPU alternates between computation and I/O wait, half the time idle.

## Q3
- Prediction：State table: 5 instructions, first instruction then I/O, then repeat. Total time = 10 ticks, utilization = 50%.
- Reasoning：Same pattern as Q2, CPU and I/O take turns.

## Q4
- Prediction：State table: Switch to process B after each I/O. Overlap I/O of A with CPU of B. Total time ~7 ticks, utilization higher.
- Reasoning：Multiprogramming overlaps I/O waiting of one job with CPU work of another.

## Q5
- Prediction：State table: 2 processes, each with 5 instructions + I/O. With overlap, total time ~7 ticks, utilization >70%.
- Reasoning：When one process waits for I/O, OS runs the other process on CPU.

## Q6
- Prediction：State table: Longer I/O. Overlap still works, total time ~11 ticks, utilization lower.
- Reasoning：I/O phase is longer, so more idle time overall.

## Q7
- Prediction：State table: Three processes. I/O of one overlaps CPU of others. Total time ~7 ticks, utilization high.
- Reasoning：More processes increases chance to keep CPU busy during I/O waits.

## Q8
- Prediction：State table: Switch on I/O start, and switch on I/O completion. Max overlap between I/O and CPU work. Total time ~7, utilization =6/7≈85.71%
- Reasoning：Combines two rules: switch when I/O starts, and wake up process immediately once I/O finishes.
