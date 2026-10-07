# OSTEP Ch.4 Homework Answers

## Q1
- Prediction / 预测:100%
- Reasoning / 理由: Instructions execute sequentially. When an I/O instruction runs, the process blocks and CPU stays idle until I/O completes.
- Verified result / 验证结果: 1        RUN:cpu         READY             1          
  2        RUN:cpu         READY             1          
  3        RUN:cpu         READY             1          
  4        RUN:cpu         READY             1          
  5        RUN:cpu         READY             1          
  6           DONE       RUN:cpu             1          
  7           DONE       RUN:cpu             1          
  8           DONE       RUN:cpu             1          
  9           DONE       RUN:cpu             1          
 10           DONE       RUN:cpu             1          

Stats: Total Time 10
Stats: CPU Busy 10 (100.00%)
Stats: IO Busy  0 (0.00%)

- Analysis / 分析:Both processes only contain CPU instructions with no I/O operations. Process 0 runs first, and then process 1 starts after process 0 finishes. The CPU remains busy the whole time, with 100% CPU utilization, which matches my prediction.

## Q2
- Prediction / 预测:cpu50%
- Reasoning / 理由: Longer I/O time increases CPU idle time, which reduces CPU utilization.
- Verified result / 验证结果: 1        RUN:cpu         READY             1          
  2        RUN:cpu         READY             1          
  3        RUN:cpu         READY             1          
  4        RUN:cpu         READY             1          
  5           DONE        RUN:io             1          
  6           DONE       BLOCKED                           1
  7           DONE       BLOCKED                           1
  8           DONE       BLOCKED                           1
  9           DONE       BLOCKED                           1
 10           DONE       BLOCKED                           1
 11*          DONE   RUN:io_done             1          

Stats: Total Time 11
Stats: CPU Busy 6 (54.55%)
Stats: IO Busy  5 (45.45%)

- Analysis / 分析:Process 0 runs 4 CPU instructions then triggers an I/O. While waiting for I/O, the CPU switches to run process 1. The CPU utilization is less than 100% due to I/O waiting time. This simulated result differs from my initial prediction.

## Q3
- Prediction / 预测:83.33%
- Reasoning / 理由:While one process waits for I/O, CPU can run instructions of the other process to overlap computation and I/O.
- Verified result / 验证结果: 1         RUN:io         READY             1          
  2        BLOCKED       RUN:cpu             1             1
  3        BLOCKED       RUN:cpu             1             1
  4        BLOCKED       RUN:cpu             1             1
  5        BLOCKED       RUN:cpu             1             1
  6        BLOCKED          DONE                           1
  7*   RUN:io_done          DONE             1          

Stats: Total Time 7
Stats: CPU Busy 6 (85.71%)
Stats: IO Busy  5 (71.43%)
- Analysis / 分析:Process 0 starts and immediately issues an I/O request. While process 0 waits for I/O, the CPU switches to execute process 1. After the I/O completes, the system switches back to process 0. This simulated result differs from my initial prediction.

## Q4
- Prediction / 预测:50%
- Reasoning / 理由Adding more processes lets CPU switch to ready tasks when one process waits for I/O, improving utilization.
- Verified result / 验证结果: 1         RUN:io         READY             1          
  2        BLOCKED         READY                           1
  3        BLOCKED         READY                           1
  4        BLOCKED         READY                           1
  5        BLOCKED         READY                           1
  6        BLOCKED         READY                           1
  7*   RUN:io_done         READY             1          
  8           DONE       RUN:cpu             1          
  9           DONE       RUN:cpu             1          
 10           DONE       RUN:cpu             1          
 11           DONE       RUN:cpu             1          

Stats: Total Time 11
Stats: CPU Busy 6 (54.55%)
Stats: IO Busy  5 (45.45%)


- Analysis / 分析:When process 0 waits for I/O, the CPU can run process 1. Both CPU busy time and I/O busy time exist, so CPU utilization is 54.55%. This simulated result differs from my initial prediction.

## Q5
- Prediction / 预测:84%
- Reasoning / 理由:Reducing I/O operations cuts blocking time, keeping the CPU busy for longer time.
- Verified result / 验证结果: 1         RUN:io         READY             1          
  2        BLOCKED       RUN:cpu             1             1
  3        BLOCKED       RUN:cpu             1             1
  4        BLOCKED       RUN:cpu             1             1
  5        BLOCKED       RUN:cpu             1             1
  6        BLOCKED          DONE                           1
  7*   RUN:io_done          DONE             1          

Stats: Total Time 7
Stats: CPU Busy 6 (85.71%)
Stats: IO Busy  5 (71.43%)
- Analysis / 分析:The two processes overlap CPU execution and I/O operations. The total time is 7 time units, and the CPU utilization reaches 85.71%. This simulated result differs from my initial prediction.

## Q6
- Prediction / 预测:70%
- Reasoning / 理由: Scheduling policies change context switch timing, which affects total execution time and utilization.
- Verified result / 验证结果: 1         RUN:io         READY         READY         READY             1          
  2        BLOCKED       RUN:cpu         READY         READY             1             1
  3        BLOCKED       RUN:cpu         READY         READY             1             1
  4        BLOCKED       RUN:cpu         READY         READY             1             1
  5        BLOCKED       RUN:cpu         READY         READY             1             1
  6        BLOCKED       RUN:cpu         READY         READY             1             1
  7*         READY          DONE       RUN:cpu         READY             1          
  8          READY          DONE       RUN:cpu         READY             1          
  9          READY          DONE       RUN:cpu         READY             1          
 10          READY          DONE       RUN:cpu         READY             1          
 11          READY          DONE       RUN:cpu         READY             1          
 12          READY          DONE          DONE       RUN:cpu             1          
 13          READY          DONE          DONE       RUN:cpu             1          
 14          READY          DONE          DONE       RUN:cpu             1          
 15          READY          DONE          DONE       RUN:cpu             1          
 16          READY          DONE          DONE       RUN:cpu             1          
 17    RUN:io_done          DONE          DONE          DONE             1          
 18         RUN:io          DONE          DONE          DONE             1          
 19        BLOCKED          DONE          DONE          DONE                           1
 20        BLOCKED          DONE          DONE          DONE                           1
 21        BLOCKED          DONE          DONE          DONE                           1
 22        BLOCKED          DONE          DONE          DONE                           1
 23        BLOCKED          DONE          DONE          DONE                           1
 24*   RUN:io_done          DONE          DONE          DONE             1          
 25         RUN:io          DONE          DONE          DONE             1          
 26        BLOCKED          DONE          DONE          DONE                           1
 27        BLOCKED          DONE          DONE          DONE                           1
 28        BLOCKED          DONE          DONE          DONE                           1
 29        BLOCKED          DONE          DONE          DONE                           1
 30        BLOCKED          DONE          DONE          DONE                           1
 31*   RUN:io_done          DONE          DONE          DONE             1          

Stats: Total Time 31
Stats: CPU Busy 21 (67.74%)
Stats: IO Busy  15 (48.39%)
- Analysis / 分析:With the switch-on-end scheduling rule, context switching only happens when a process finishes. The total runtime and CPU utilization change. This simulated result differs from my initial prediction.

## Q7
- Prediction / 预测:50%
- Reasoning / 理由: Immediate preemption after I/O completion rearranges task execution order and changes CPU utilization.
- Verified result / 验证结果:Time        PID:0      PID:1      PID:2      PID:3       CPU       IOs
1         RUN:io      READY      READY      READY         1         1
2        BLOCKED    RUN:cpu      READY      READY         1         1
3        BLOCKED    RUN:cpu      READY      READY         1         1
4        BLOCKED    RUN:cpu      READY      READY         1         1
5        BLOCKED    RUN:cpu      READY      READY         1         1
6        BLOCKED    RUN:cpu      READY      READY         1         1
7        BLOCKED       DONE    RUN:cpu      READY         1         1
8        BLOCKED       DONE    RUN:cpu      READY         1         1
9        BLOCKED       DONE    RUN:cpu      READY         1         1
10       BLOCKED       DONE    RUN:cpu      READY         1         1
11       BLOCKED       DONE    RUN:cpu      READY         1         1
12       BLOCKED       DONE       DONE    RUN:cpu         1         1
13       BLOCKED       DONE       DONE    RUN:cpu         1         1
14       BLOCKED       DONE       DONE    RUN:cpu         1         1
15       BLOCKED       DONE       DONE    RUN:cpu         1         1
16       BLOCKED       DONE       DONE    RUN:cpu         1         1
17         DONE        DONE       DONE       DONE         1         1

Stats: Total Time 17
Stats: CPU Busy 17 (100.00%)
Stats: IO Busy  3 (17.65%)
- Analysis / 分析:We test two I/O completion strategies: IO_RUN_LATER and IO_RUN_IMMEDIATE.
In IO_RUN_LATER, when I/O finishes, the process will not run immediately; the scheduler continues running the current CPU-bound process.
In IO_RUN_IMMEDIATE, the process which just finished I/O will run immediately.
Our simulator version does not support IO_RUN_IMMEDIATE, so we only obtain the result of IO_RUN_LATER.
The total time is 17 time units and CPU utilization reaches 100%.
This simulated result differs from my initial prediction.



## Q8
- Prediction / 预测:58%
- Reasoning / 理由:Different random seeds generate different scheduling sequences, leading to different CPU utilization results
- Verified result / 验证结果:Under the default SWITCH_ON_IO policy, when a process triggers I/O and becomes blocked, the CPU switches to another ready process right away. The total running time is shorter, and the CPU utilization is higher.
- Analysis / 分析:When a process waits for I/O, the operating system switches the CPU to the other ready task. The I/O waiting time is reused to run another process. This avoids idle CPU time and improves CPU utilization.