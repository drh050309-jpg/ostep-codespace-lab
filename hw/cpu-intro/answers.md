# OSTEP Ch.4 Homework Answers

## Q1
- Prediction / 预测:100%
- Reasoning / 理由: Instructions execute sequentially. When an I/O instruction runs, the process blocks and CPU stays idle until I/O completes.
- Verified result / 验证结果:
- Analysis / 分析:

## Q2
- Prediction / 预测:cpu50%
- Reasoning / 理由: Longer I/O time increases CPU idle time, which reduces CPU utilization.
- Verified result / 验证结果:
- Analysis / 分析:

## Q3
- Prediction / 预测:83.33%
- Reasoning / 理由:While one process waits for I/O, CPU can run instructions of the other process to overlap computation and I/O.
- Verified result / 验证结果:
- Analysis / 分析:

## Q4
- Prediction / 预测:50%
- Reasoning / 理由Adding more processes lets CPU switch to ready tasks when one process waits for I/O, improving utilization.
- Verified result / 验证结果:
- Analysis / 分析:

## Q5
- Prediction / 预测:84%
- Reasoning / 理由:Reducing I/O operations cuts blocking time, keeping the CPU busy for longer time.
- Verified result / 验证结果:
- Analysis / 分析:

## Q6
- Prediction / 预测:70%
- Reasoning / 理由: Scheduling policies change context switch timing, which affects total execution time and utilization.
- Verified result / 验证结果:
- Analysis / 分析:

## Q7
- Prediction / 预测:50%
- Reasoning / 理由: Immediate preemption after I/O completion rearranges task execution order and changes CPU utilization.
- Verified result / 验证结果:
- Analysis / 分析:


## Q8
- Prediction / 预测:58%
- Reasoning / 理由:Different random seeds generate different scheduling sequences, leading to different CPU utilization results
- Verified result / 验证结果:
- Analysis / 分析: