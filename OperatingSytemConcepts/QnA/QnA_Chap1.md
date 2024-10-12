# Chapter 1 Introduction
CHAPTER OBJECTIVES
- Describe the general organization of a computer system and the role of
interrupts.
- Describe the components in a modern multiprocessor computer system.
- Illustrate the transition from user mode to kernel mode.
- Discuss how operating systems are used in various computing environments.
- Provide examples of free and open-source operating systems.

## 1. What Operating Systems Do
운영체제(Operating System): 컴퓨터의 하드웨어를 관리하고, 하드웨어와 소프트웨어, 사용자를 매개하는 프로그램

하는 일 : 프로그램들이 동작할 수 있는 환경을 제공, 하드웨어 사용을 편성, 조작. 사용자, 시스템 관점에서 볼 수 있더라~

## 2. Computer-System Organization
구성 : 여러개의 CPU, Device Controller
Common bus로 이어져서 메모를 공유
Common bus : 데이터 이동 통로

## 3. Computer-System Architecture
core : 명령어 실행, 데이터 local 저장하는 요소 (register를 가짐) 
main CPU with core: 범용 명령어 셋을 실행

## 4. Operating-System Operations
Initial program (bootstrap program) 
컴퓨터를 실행하기 위해서는 초기 프로그램인 boorstarp program을 실행해야 합니다. 
비 휘발성인 firmware로 HW에 저장되어 부팅 시 실행됩니다. 
과정을 살펴보면 다음과 같습니다. 
- 시스템을 초기화 시킨다. (CPU register, device controller, memory contents) 
- OS 커널을 찾아서 메모리에 로드한다. 
- 커널이 로드되어 실행되면 시스템과 사용자에게 서비스를 제공한다. "systemd"이라는 프로그램은 리눅스에서 가장 먼저 실행되며, 다 른 daemon을 시작한다 

Events (이벤트의 처리) 이벤트는 interrupt를 발생시켜 신호를 보냄.
- Hardware interrupt: device에서 발생 
- Trap or Exception: software error, system call(CPU의 도움이 필요한 경우 OS가 필요)

## 5. Resource Management
program은 디스크에 저장된 파일이고(수동적), process는 메모리 위에서 실행되는 program.(능동적)

## 6. Security and Protection

## 7. Virtualization
가상화(Virtualization)

가상화 기술은 하나의 컴퓨터 하드웨어 위에서 여러개의 다른 운영체제를 실행하는 기술. 가상화 기술을 사용하면 하드웨어에 VMM(Virtual Machine Manager)를 올리게 됨. VMM의 종류로는 Vmare, XEN, WSL 등이 존재.

## 8. Distributed Systems

## 9. Kernel Data Stuructures
- 리스트, 스택, 큐
- 트리
- 해시함수, 맵
- 비트맵

## 10. Computing Environments
- 전통적인 계산 환경의 경계가 흐려지고 있다. 
- Mobile Computing은 휴대용 스마트폰과 태블릿 컴퓨터의 계산을 말한다. 
- 분산 시스템은 물리적으로 떨어져 있는 컴퓨터들의 집합이다. 
- 분산 시스템의 컴퓨터들은 사용자가 시스템 내의 다양한 자원들을 접근할 수 있도록 네트워크로 연결되어 있다. 
- 가상화(Virtualization)은 운영체제가 다른 운영체제 내에서의 하나의 Application처럼 수행될 수 있게 한다. 
- 클라우드 컴퓨팅은 computing, storage, application까지 네트워크를 통한 서비스로 제 공하는 계산 유형이다.

## 11. Free and Open-Source Operating Systems
- 오픈소스 운영체제는 컴파일된 Binary code보다는 Source Code 형태로 받을 수 있는 운 영체제를 의미한다. 
- 오픈소스의 대표적인 운영체제로는 Linux, Solaris 등이 있다.

# +
An operating system is software that manages the computer hardware, as
well as providing an environment for application programs to run.
• Interrupts are a key way in which hardware interacts with the operating
system. A hardware device triggers an interrupt by sending a signal to the
CPU to alert the CPU that some event requires attention. The interrupt is
managed by the interrupt handler.
• For a computer to do its job of executing programs, the programs must be
in main memory, which is the only large storage area that the processor
can access directly.
• The main memory is usually a volatile storage device that loses its contents
when power is turned off or lost.
52 Chapter 1 Introduction
• Nonvolatile storage is an extension of main memory and is capable of
holding large quantities of data permanently.
• The most common nonvolatile storage device is a hard disk, which can
provide storage of both programs and data.
• The wide variety of storage systems in a computer system can be organized
in a hierarchy according to speed and cost. The higher levels are expensive,
but they are fast. As we move down the hierarchy, the cost per bit generally
decreases, whereas the access time generally increases.
• Modern computer architectures are multiprocessor systems in which each
CPU contains several computing cores.
• To best utilize the CPU, modern operating systems employ multiprogramming, which allows several jobs to be in memory at the same time, thus
ensuring that the CPU always has a job to execute.
• Multitasking is an extension of multiprogramming wherein CPU scheduling algorithms rapidly switch between processes, providing users with a
fast response time.
• To prevent user programs from interfering with the proper operation of
the system, the system hardware has two modes: user mode and kernel
mode.
• Various instructions are privileged and can be executed only in kernel
mode. Examples include the instruction to switch to kernel mode, I/O
control, timer management, and interrupt management.
• A process is the fundamental unit of work in an operating system. Process management includes creating and deleting processes and providing
mechanisms for processes to communicate and synchronize with each
other.
• An operating system manages memory by keeping track of what parts of
memory are being used and by whom. It is also responsible for dynamically allocating and freeing memory space.
• Storage space is managed by the operating system; this includes providing
file systems for representing files and directories and managing space on
mass-storage devices.
• Operating systems provide mechanisms for protecting and securing the
operating system and users. Protection measures control the access of
processes or users to the resources made available by the computer system.
• Virtualization involves abstracting a computer’s hardware into several
different execution environments.
• Data structures that are used in an operating system include lists, stacks,
queues, trees, and maps.
• Computing takes place in a variety of environments, including traditional
computing, mobile computing, client–server systems, peer-to-peer systems, cloud computing, and real-time embedded systems.

# ++
- 운영체제는 컴퓨터 하드웨어를 관리하고 응용 프로그램이 실행될 수 있는 환경을 제공하는 소프트웨어입니다.

- 인터럽트는 하드웨어가 운영체제와 상호작용하는 주요 방법 중 하나입니다. 하드웨어 장치는 CPU에 신호를 보내 특정 이벤트가 주목을 필요로 함을 알림으로써 인터럽트를 발생시킵니다. 인터럽트는 인터럽트 핸들러에 의해 관리됩니다.
- 프로그램이 실행되기 위해서는 메인 메모리에 존재해야 하며, 메인 메모리는 프로세서가 직접 접근할 수 있는 유일한 큰 저장 공간입니다.
- 메인 메모리는 일반적으로 휘발성 저장 장치로, 전원이 꺼지거나 잃어버리면 내용이 사라집니다.
- 비휘발성 저장 장치는 메인 메모리의 확장으로, 대량의 데이터를 영구적으로 저장할 수 있습니다.
- 가장 일반적인 비휘발성 저장 장치는 하드 디스크로, 프로그램과 데이터를 모두 저장할 수 있습니다.
- 컴퓨터 시스템의 다양한 저장 시스템은 속도와 비용에 따라 계층적으로 조직할 수 있습니다. 상위 수준은 비싸지만 빠르며, 계층을 내려갈수록 비트당 비용은 일반적으로 감소하고 접근 시간은 증가합니다.
- 현대 컴퓨터 아키텍처는 각 CPU가 여러 컴퓨팅 코어를 포함하는 다중 프로세서 시스템입니다.
- CPU를 최적으로 활용하기 위해 현대 운영체제는 다중 프로그래밍을 사용하여 여러 작업이 메모리에 동시에 존재하도록 하여 CPU가 항상 실행할 작업이 있도록 합니다.
- 다중 작업은 CPU 스케줄링 알고리즘이 프로세스 간에 빠르게 전환하여 사용자에게 빠른 응답 시간을 제공하는 다중 프로그래밍의 확장입니다.
- 사용자 프로그램이 시스템의 정상 작동에 간섭하지 않도록 시스템 하드웨어에는 사용자 모드와 커널 모드의 두 가지 모드가 있습니다.
- 다양한 명령어는 특권 명령어로, 커널 모드에서만 실행될 수 있습니다. 예를 들어, 커널 모드로 전환하는 명령어, I/O 제어, 타이머 관리, 인터럽트 관리 등이 있습니다.
- 프로세스는 운영체제에서의 기본 작업 단위입니다. 프로세스 관리는 프로세스를 생성하고 삭제하며, 프로세스 간의 통신 및 동기화를 위한 메커니즘을 제공합니다.
- 운영체제는 메모리를 관리하며, 어떤 부분이 누가 사용하고 있는지를 추적합니다. 또한 동적으로 메모리 공간을 할당하고 해제하는 역할을 합니다.
- 저장 공간은 운영체제가 관리하며, 파일과 디렉토리를 표현하는 파일 시스템을 제공하고 대용량 저장 장치의 공간을 관리합니다.
- 운영체제는 시스템과 사용자를 보호하고 안전하게 하기 위한 메커니즘을 제공합니다. 보호 조치는 프로세스나 사용자가 컴퓨터 시스템에서 제공하는 자원에 접근하는 것을 제어합니다.
- 가상화는 컴퓨터 하드웨어를 여러 개의 실행 환경으로 추상화하는 것을 의미합니다.
- 운영체제에서 사용되는 데이터 구조에는 리스트, 스택, 큐, 트리 및 맵이 포함됩니다.
- 컴퓨팅은 전통적인 컴퓨팅, 모바일 컴퓨팅, 클라이언트-서버 시스템, 피어 투 피어 시스템, 클라우드 컴퓨팅 및 실시간 임베디드 시스템 등 다양한 환경에서 이루어집니다.

# Words
1. intermediary
2. vary
3. accomplishing
4. allocate
5. well-delineated