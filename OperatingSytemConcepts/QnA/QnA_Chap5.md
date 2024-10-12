# Chapter 5 CPU Scheduling
• Describe various CPU scheduling algorithms.
• Assess CPU scheduling algorithms based on scheduling criteria.
• Explain the issues related to multiprocessor and multicore scheduling.
• Describe various real-time scheduling algorithms.
• Describe the scheduling algorithms used in the Windows, Linux, and
Solaris operating systems.
• Apply modeling and simulations to evaluate CPU scheduling algorithms.
• Design a program that implements several different CPU scheduling algorithms.

# 1 Basic Concepts

# 2 Scheduling Criteria

# 3 Scheduling Algorithms

# 4 Thread Scheduling

# 5 Multi-Processor Scheduling

# 6 Real-Time CPU Scheduling

# 7 Operating-System Examples

# 8 Algorithm Evaluation

# +
• CPU scheduling is the task of selecting a waiting process from the ready
queue and allocating the CPU to it. The CPU is allocated to the selected
process by the dispatcher.
• Scheduling algorithms may be either preemptive (where the CPU can be
taken away from a process) or nonpreemptive (where a process must
voluntarily relinquish control of the CPU). Almost all modern operating
systems are preemptive.
• Scheduling algorithms can be evaluated according to the following five
criteria: (1) CPU utilization, (2) throughput, (3) turnaround time, (4) waiting
time, and (5) response time.
• First-come, first-served (FCFS) scheduling is the simplest scheduling algorithm, but it can cause short processes to wait for very long processes.
• Shortest-job-first (SJF) scheduling is provably optimal, providing the shortest average waiting time. Implementing SJF scheduling is difficult, however, because predicting the length of the next CPU burst is difficult.
• Round-robin (RR) scheduling allocates the CPU to each process for a time
quantum. If the process does not relinquish the CPU before its time quantum expires, the process is preempted, and another process is scheduled
to run for a time quantum.
• Priority scheduling assigns each process a priority, and the CPU is allocated
to the process with the highest priority. Processes with the same priority
can be scheduled in FCFS order or using RR scheduling.
• Multilevel queue scheduling partitions processes into several separate
queues arranged by priority, and the scheduler executes the processes in
the highest-priority queue. Different scheduling algorithms may be used
in each queue.
• Multilevel feedback queues are similar to multilevel queues, except that a
process may migrate between different queues.
• Multicore processors place one or more CPUs on the same physical chip,
and each CPU may have more than one hardware thread. From the perspective of the operating system, each hardware thread appears to be a
logical CPU.
• Load balancing on multicore systems equalizes loads between CPU cores,
although migrating threads between cores to balance loads may invalidate
cache contents and therefore may increase memory access times.
• Soft real-time scheduling gives priority to real-time tasks over non-realtime tasks. Hard real-time scheduling provides timing guarantees for realtime tasks,
• Rate-monotonic real-time scheduling schedules periodic tasks using a
static priority policy with preemption.
Practice Exercises 251
• Earliest-deadline-first (EDF) scheduling assigns priorities according to
deadline. The earlier the deadline, the higher the priority; the later the
deadline, the lower the priority.
• Proportional share scheduling allocates T shares among all applications. If
an application is allocated N shares of time, it is ensured of having N∕T of
the total processor time.
• Linux uses the completely fair scheduler (CFS), which assigns a proportion
of CPU processing time to each task. The proportion is based on the virtual
runtime (vruntime) value associated with each task.
• Windows scheduling uses a preemptive, 32-level priority scheme to determine the order of thread scheduling.
• Solaris identifies six unique scheduling classes that are mapped to a global
priority. CPU-intensive threads are generally assigned lower priorities
(and longer time quantums), and I/O-bound threads are usually assigned
higher priorities (with shorter time quantums.)
• Modeling and simulations can be used to evaluate a CPU scheduling algorithm.

# ++
CPU 스케줄링은 대기 중인 프로세스 중에서 준비 큐에서 하나를 선택하고 CPU를 할당하는 작업입니다. 선택된 프로세스에게 CPU는 디스패처(dispatcher)에 의해 할당됩니다.

스케줄링 알고리즘은 선점형(preemptive)일 수도 있고 비선점형(nonpreemptive)일 수도 있습니다. 선점형 알고리즘에서는 CPU를 프로세스에서 빼앗을 수 있지만, 비선점형에서는 프로세스가 자발적으로 CPU 제어를 포기해야 합니다. 거의 모든 현대 운영체제는 선점형입니다.
스케줄링 알고리즘은 다음의 다섯 가지 기준에 따라 평가될 수 있습니다: (1) CPU 활용도, (2) 처리량(throughput), (3) 반환 시간(turnaround time), (4) 대기 시간(waiting time), (5) 응답 시간(response time).
선입선출(FCFS) 스케줄링은 가장 간단한 스케줄링 알고리즘이지만, 짧은 프로세스가 긴 프로세스 때문에 오랫동안 대기해야 할 수 있습니다.
최단 작업 우선(SJF) 스케줄링은 증명 가능한 최적의 알고리즘으로, 평균 대기 시간을 가장 짧게 제공합니다. 그러나 SJF 스케줄링을 구현하기는 어렵고, 다음 CPU 작업의 길이를 예측하는 것이 어렵기 때문입니다.
라운드 로빈(RR) 스케줄링은 각 프로세스에 대해 시간 할당량(time quantum)을 할당합니다. 프로세스가 자신의 시간 할당량이 만료되기 전에 CPU를 relinquish하지 않으면, 해당 프로세스는 선점되고 다른 프로세스가 시간 할당량을 위해 실행됩니다.
우선 순위 스케줄링은 각 프로세스에 우선 순위를 부여하고, CPU는 가장 높은 우선 순위를 가진 프로세스에 할당됩니다. 동일한 우선 순위를 가진 프로세스는 FCFS 순서로 또는 RR 스케줄링을 사용하여 스케줄될 수 있습니다.
다중 레벨 큐 스케줄링은 프로세스를 여러 개의 별도 큐로 나누어 우선 순위에 따라 정렬하며, 스케줄러는 가장 높은 우선 순위 큐에서 프로세스를 실행합니다. 각 큐에서는 다른 스케줄링 알고리즘을 사용할 수 있습니다.
다중 레벨 피드백 큐는 다중 레벨 큐와 유사하지만, 프로세스가 서로 다른 큐 간에 이동할 수 있습니다.
다중 코어 프로세서는 동일한 물리적 칩에 하나 이상의 CPU를 배치하며, 각 CPU는 하나 이상의 하드웨어 스레드를 가질 수 있습니다. 운영체제 관점에서 각 하드웨어 스레드는 논리적 CPU처럼 보입니다.
다중 코어 시스템에서 로드 밸런싱은 CPU 코어 간의 부하를 균등하게 하며, 부하를 균형 맞추기 위해 스레드를 코어 간에 이동하면 캐시 내용이 무효화될 수 있고, 따라서 메모리 접근 시간이 증가할 수 있습니다.
소프트 실시간 스케줄링은 비실시간 작업보다 실시간 작업에 우선 순위를 부여합니다. 하드 실시간 스케줄링은 실시간 작업에 대한 시간 보장을 제공합니다.
**비율 단조(real-time scheduling)**은 정적 우선 순위 정책을 사용하여 주기적인 작업을 스케줄링합니다.
가장 이른 마감 기한 우선(EDF) 스케줄링은 마감 기한에 따라 우선 순위를 부여합니다. 마감 기한이 이르면 우선 순위가 높고, 마감 기한이 늦으면 우선 순위가 낮아집니다.
비례 공유 스케줄링은 모든 애플리케이션에 T shares를 할당합니다. 애플리케이션에 N shares의 시간이 할당되면 전체 프로세서 시간의 N/T를 보장받게 됩니다.
리눅스는 **완전 공정 스케줄러(CFS)**를 사용하여 각 작업에 CPU 처리 시간을 할당합니다. 이 비율은 각 작업과 관련된 가상 런타임(vruntime) 값을 기반으로 합니다.
Windows 스케줄링은 스레드 스케줄링 순서를 결정하기 위해 선점형 32단계 우선 순위 체계를 사용합니다.
Solaris는 글로벌 우선 순위에 매핑된 여섯 가지 고유한 스케줄링 클래스를 식별합니다. CPU 집약적 스레드는 일반적으로 낮은 우선 순위(및 긴 시간 할당량)를 부여받고, I/O 집약적 스레드는 일반적으로 높은 우선 순위(및 짧은 시간 할당량)를 부여받습니다.
모델링 및 시뮬레이션은 CPU 스케줄링 알고리즘을 평가하는 데 사용할 수 있습니다.