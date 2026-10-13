Q1 
  Job   0 -- Response: 0.00  Turnaround 200.00  Wait 0.00
  Job   1 -- Response: 200.00  Turnaround 400.00  Wait 200.00
  Job   2 -- Response: 400.00  Turnaround 600.00  Wait 400.00
Q2
  Job   0 -- Response: 0.00  Turnaround 100.00  Wait 0.00
  Job   1 -- Response: 100.00  Turnaround 300.00  Wait 100.00
  Job   2 -- Response: 300.00  Turnaround 600.00  Wait 300.00
Q3
  Job   0 -- Response: 0.00  Turnaround 298.00  Wait 198.00
  Job   1 -- Response: 1.00  Turnaround 499.00  Wait 299.00
  Job   2 -- Response: 2.00  Turnaround 600.00  Wait 300.00
Q4 
Answer: SJF has the same turnaround time as FIFO when jobs arrive in shortest-to-longer order, or all jobs have equal running time
Q5
They share the same response time if RR’s time quantum ≥ the runtime of the longest job.
A job will finish entirely without preemption after acquiring the CPU, so RR will not switch between jobs repeatedly.

Q6
For SJF: The response time of longer jobs increases. Long jobs have to wait for all shorter arrived jobs to complete before starting.
The response time of longer jobs increases. In SJF, shorter jobs have higher priority. A long job cannot start running until all shorter arrived jobs finish execution.

We use two simulator test cases to demonstrate this trend
Q7
As the time quantum increases, the worst‑case response time of RR increases.
When the quantum becomes larger, each job occupies the CPU for a longer duration in every round. Other waiting jobs must wait a longer period before they get their turn to run
The worst‑case response time of RR grows as the quantum increases.
If all N jobs arrive at time zero, worst‑case response time = (N-1)\times quantum