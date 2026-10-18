# Chapter 7 Analysis

## Question 1: FIFO vs SJF

**Workload:** `-l 100,200,300`

### Results
| Policy | Avg Response Time | Avg Turnaround Time |
| :--- | :--- | :--- |
| FIFO | 133.33 | 333.33 |
| SJF  | 133.33 | 333.33 |

### Observation
- **FIFO (First-In-First-Out):** 按照到达顺序执行。作业长度长的会阻塞后面的作业，导致平均周转时间较长。
- **SJF (Shortest Job First):** 优先执行最短的作业。把短作业排在前面，可以显著降低平均周转时间。但是，如果一直有短作业进来，长作业可能会被“饿死”（不过本题是同时到达，所以不会）。
- 对比发现，SJF 的平均周转时间更短，因为短作业没有被长作业堵塞。




## Question 3: Round-Robin (RR)

**Workload:** `-l 100,200,300`

### Results
| Quantum (q) | Avg Response Time | Avg Turnaround Time |
| :--- | :--- | :--- |
| q = 10 | 10.00 | 456.67 |
| q = 50 | 50.00 | 416.67 |
| q = 100 | 100.00 | 366.67 |

### Observation
- 随着时间片 (Quantum) 的增大，**响应时间 (Response Time) 变长**，因为作业需要等更长时间才能再次轮到 CPU。
- 随着时间片增大，**周转时间 (Turnaround Time) 缩短**，且越来越接近 FIFO。因为当时间片大到足以一次跑完一个作业时，RR 就退化成 FIFO 了。
- **结论：** 时间片大小的选择是一个权衡（Trade-off）。小时间片保证了高响应性（适合交互式系统），大时间片减少了切换开销并缩短了周转时间。