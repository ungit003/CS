# Chapter 3 Processes
- Identify the separate components of a process and illustrate how they are
represented and scheduled in an operating system.
- Describe how processes are created and terminated in an operating system, including developing programs using the appropriate system calls
that perform these operations.
- Describe and contrast interprocess communication using shared memory
and message passing.
- Design programs that use pipes and POSIX shared memory to perform
interprocess communication.
- Describe client – server communication using sockets and remote procedure calls.
- Design kernel modules that interact with the Linux operating system.

# 1 Process Concept

# 2 Process Scheduling

# 3 Operations on Processes

# 4 Interprocess Communication

# 5 IPC in Shared-Memory Systems

# 6 IPC in Message-Passing Systems

# 7 Examples of IPC Systems

# 8 Communication in Client – Server Systems

# +
- A process is a program in execution, and the status of the current activity of
a process is represented by the program counter, as well as other registers.
- The layout of a process in memory is represented by four different sections:
(1) text, (2) data, (3) heap, and (4) stack.
- As a process executes, it changes state. There are four general states of a
process: (1) ready, (2) running, (3) waiting, and (4) terminated.
- A process control block (PCB) is the kernel data structure that represents a
process in an operating system.
- The role of the process scheduler is to select an available process to run on
a CPU.
- An operating system performs a context switch when it switches from
running one process to running another.
154 Chapter 3 Processes
- The fork() and CreateProcess() system calls are used to create processes on UNIX and Windows systems, respectively.
- When shared memory is used for communication between processes, two
(or more) processes share the same region of memory. POSIX provides an
API for shared memory.
- Two processes may communicate by exchanging messages with one
another using message passing. The Mach operating system uses message
passing as its primary form of interprocess communication. Windows
provides a form of message passing as well.
- A pipe provides a conduit for two processes to communicate. There are
two forms of pipes, ordinary and named. Ordinary pipes are designed for
communication between processes that have a parent–child relationship.
Named pipes are more general and allow several processes to communicate.
- UNIX systems provide ordinary pipes through the pipe() system call.
Ordinary pipes have a read end and a write end. A parent process can, for
example, send data to the pipe using its write end, and the child process
can read it from its read end. Named pipes in UNIX are termed FIFOs.
- Windows systems also provide two forms of pipes—anonymous and
named pipes. Anonymous pipes are similar to UNIX ordinary pipes. They
are unidirectional and employ parent–child relationships between the
communicating processes. Named pipes offer a richer form of interprocess
communication than the UNIX counterpart, FIFOs.
- Two common forms of client–server communication are sockets and
remote procedure calls (RPCs). Sockets allow two processes on different
machines to communicate over a network. RPCs abstract the concept of
function (procedure) calls in such a way that a function can be invoked on
another process that may reside on a separate computer.
- The Android operating system uses RPCs

# ++
- 프로세스는 실행 중인 프로그램이며, 프로세스의 현재 활동 상태는 프로그램 카운터 및 기타 레지스터에 의해 나타납니다.

- 프로세스의 메모리 배치는 네 가지 서로 다른 섹션으로 구성됩니다: (1) 텍스트, (2) 데이터, (3) 힙, (4) 스택.
- 프로세스가 실행됨에 따라 상태가 변경됩니다. 프로세스의 일반적인 상태는 (1) 준비(ready), (2) 실행(running), (3) 대기(waiting), (4) 종료(terminated)입니다.
- **프로세스 제어 블록(PCB)**은 운영체제에서 프로세스를 나타내는 커널 데이터 구조입니다.
- 프로세스 스케줄러의 역할은 CPU에서 실행할 수 있는 프로세스를 선택하는 것입니다.
- 운영체제가 하나의 프로세스에서 다른 프로세스로 전환할 때 컨텍스트 스위치를 수행합니다.
- UNIX 시스템에서는 fork() 시스템 호출을 사용하여 프로세스를 생성하고, Windows 시스템에서는 CreateProcess()를 사용합니다.
- 프로세스 간의 통신에 공유 메모리를 사용하는 경우, 두 개 이상의 프로세스가 동일한 메모리 영역을 공유합니다. POSIX는 공유 메모리를 위한 API를 제공합니다.
- 두 프로세스는 메시지 전송을 통해 서로 통신할 수 있습니다. Mach 운영체제는 메시지 전송을 주요 인터프로세스 통신 형태로 사용합니다. Windows도 메시지 전송 형태를 제공합니다.
- **파이프(pipe)**는 두 프로세스가 통신할 수 있도록 하는 통로를 제공합니다. 파이프에는 일반 파이프(ordinary pipe)와 명명된 파이프(named pipe) 두 가지 형태가 있습니다. 일반 파이프는 부모-자식 관계에 있는 프로세스 간의 통신을 위해 설계되었습니다. 명명된 파이프는 보다 일반적이며 여러 프로세스 간의 통신을 허용합니다.
- UNIX 시스템은 pipe() 시스템 호출을 통해 일반 파이프를 제공합니다. 일반 파이프는 읽기 끝(read end)과 쓰기 끝(write end)이 있습니다. 예를 들어, 부모 프로세스는 쓰기 끝을 사용하여 파이프에 데이터를 보낼 수 있고, 자식 프로세스는 읽기 끝을 통해 이를 읽을 수 있습니다. UNIX의 명명된 파이프는 FIFO(First In, First Out)라고 불립니다.
- Windows 시스템에서도 두 가지 형태의 파이프—익명 파이프(anonymous pipe)와 명명된 파이프(named pipe)를 제공합니다. 익명 파이프는 UNIX의 일반 파이프와 유사합니다. 단방향이며, 통신하는 프로세스 간의 부모-자식 관계를 사용합니다. 명명된 파이프는 UNIX의 FIFO보다 더 풍부한 형태의 인터프로세스 통신을 제공합니다.
- 클라이언트-서버 통신의 두 가지 일반적인 형태는 **소켓(sockets)**과 **원격 프로시저 호출(RPCs)**입니다. 소켓은 서로 다른 머신에 있는 두 프로세스가 네트워크를 통해 통신할 수 있게 합니다. RPC는 함수(프로시저) 호출의 개념을 추상화하여, 다른 프로세스(서로 다른 컴퓨터에 있을 수 있음)에서 함수를 호출할 수 있도록 합니다.
- 안드로이드 운영체제는 RPC를 사용합니다