## Q1
- Prediction / 预测:
State table: P0 runs for 5 cycles, then P1 runs for 5 cycles. No I/O, no blocking.
total time = 10, CPU utilization = 10/10 = 100%
- Reasoning / 理由：Both processes only use CPU instructions, no I/O. CPU keeps busy the whole time, zero idle cycles.

- Verified result / 验证结果：
- Analysis / 分析：

## Q2
- Prediction / 预测:
State table: P0 runs 4 CPU cycles. P1 runs 1 instruction then blocks for I/O. While P1 waits I/O, CPU is idle.
total time = 1 + I/O_time + 4 = 9, CPU utilization = 5/9 ≈ 55.56%
- Reasoning / 理由：P1 issues I/O and blocks. There is no other process to run during I/O wait, CPU sits idle.

- Verified result / 验证结果：
- Analysis / 分析：

## Q3
- Prediction / 预测:
State table: P0 starts I/O instruction and becomes blocked. While P0 waits for I/O, CPU runs P1’s 4 CPU instructions.
total time = 7, CPU utilization = 7/7 = 100%
- Reasoning / 理由：P0 issues I/O at time 1 and blocks. During the I/O waiting period, CPU executes P1’s four CPU instructions in parallel with I/O operation, so no idle cycles.

- Verified result / 验证结果：
- Analysis / 分析：

## Q4
- Prediction / 预测:
State table: P0 starts I/O and blocks. OS switches to P1, P1 starts I/O and blocks. Both I/O happen in parallel.
total time = 5, CPU utilization = 2/5 = 40%
- Reasoning / 理由：Two processes both issue I/O. Their I/O waits overlap. CPU only spends 2 cycles starting I/O, then idle waiting for I/O finish.

- Verified result / 验证结果：
- Analysis / 分析：

## Q5
- Prediction / 预测:
State table: P0 issues I/O and blocks, OS immediately switches to P1. P1 runs its I/O instruction. Two I/O run in parallel.
total time =5, CPU utilization = 2/5 =40%
- Reasoning / 理由：SWITCH_ON_IO means switch process right when I/O starts. I/O waits overlap, CPU only uses two cycles for starting I/O.

- Verified result / 验证结果：
- Analysis / 分析：

## Q6
- Prediction / 预测:
State table: P0 runs I/O instruction, blocks, and waits for I/O complete before switching to P1. P1 then runs its I/O. I/O cannot overlap.
total time =9, CPU utilization =2/9 ≈22.22%
- Reasoning / 理由：SWITCH_ON_END only switches after a process fully finishes. P0's I/O finishes first, then P1 starts I/O. No overlapping I/O, longer total time.

- Verified result / 验证结果：
- Analysis / 分析：

## Q7
- Prediction / 预测:
State table: P0 issues I/O and blocks. While P0 waits I/O, OS runs P1 and P2. Multiprogramming overlaps I/O and CPU work.
total time =11, CPU utilization =10/11≈90.91%
- Reasoning / 理由：When P0 waits for I/O, CPU can run P1 and P2. Most of I/O waiting time is filled with CPU computation, only a small idle cycle.

- Verified result / 验证结果：
- Analysis / 分析：

## Q8-s1
- Prediction / 预测:
State table: When I/O completes, OS does not immediately run the ready process. It waits until current running process finishes.
total time =8, CPU utilization =6/8=75%
- Reasoning / 理由：IO_RUN_LATER: I/O completes but the ready process does not run until current process ends. This creates idle cycles.

- Verified result / 验证结果：
- Analysis / 分析：

## Q8-s2
- Prediction / 预测:
State table: When I/O finishes, OS immediately switches to the ready process. No idle time.
total time =7, CPU utilization =6/7≈85.71%
- Reasoning / 理由：IO_RUN_IMMEDIATE: once I/O completes, the ready process runs right away, minimizing idle cycles.

- Verified result / 验证结果：
- Analysis / 分析：

## Q8-s3
- Prediction / 预测:
State table: Switch on I/O start, and run immediately when I/O completes. Max overlap between I/O and CPU work.
total time =7, CPU utilization =6/7≈85.71%
- Reasoning / 理由：Combines two rules: switch when I/O starts, and wake up process immediately once I/O finishes.

- Verified result / 验证结果：
- Analysis / 分析：
