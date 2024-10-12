# Chapter 2 Operating-System Structures
- Identify services provided by an operating system.
- Illustrate how system calls are used to provide operating system services.
- Compare and contrast monolithic, layered, microkernel, modular, and
hybrid strategies for designing operating systems.
- Illustrate the process for booting an operating system.
- Apply tools for monitoring operating system performance.
- Design and implement kernel modules for interacting with a Linux kernel.

# 1. Operating-System Service

# 2. User and Operating-System Interface

# 3. System Calls

# 4. System Services

# 5. Linkers and Loaders

# 6. Why Applications Are Operating-System Specific

# 7. Operating-System Design and Implementation

# 8. Operating-System Structure

# 9. Building and Booting an Operating System

# 10. Operating-System Debugging

# +
• An operating system provides an environment for the execution of programs by providing services to users and programs.
• The three primary approaches for interacting with an operating system
are (1) command interpreters, (2) graphical user interfaces, and (3) touchscreen interfaces.
• System calls provide an interface to the services made available by an operating system. Programmers use a system call’s application programming
interface (API) for accessing system-call services.
• System calls can be divided into six major categories: (1) process control,
(2) file management, (3) device management, (4) information maintenance,
(5) communications, and (6) protection.
• The standard C library provides the system-call interface for UNIX and
Linux systems.
• Operating systems also include a collection of system programs that provide utilities to users.
• A linker combines several relocatable object modules into a single binary
executable file. A loader loads the executable file into memory, where it
becomes eligible to run on an available CPU.
• There are several reasons why applications are operating-system specific.
These include different binary formats for program executables, different
instruction sets for different CPUs, and system calls that vary from one
operating system to another.
• An operating system is designed with specific goals in mind. These goals
ultimately determine the operating system’s policies. An operating system
implements these policies through specific mechanisms.
• A monolithic operating system has no structure; all functionality is provided in a single, static binary file that runs in a single address space.
Although such systems are difficult to modify, their primary benefit is
efficiency.
• A layered operating system is divided into a number of discrete layers,
where the bottom layer is the hardware interface and the highest layer is
the user interface. Although layered software systems have had some suc-
Further Reading 101
cess, this approach is generally not ideal for designing operating systems
due to performance problems.
• The microkernel approach for designing operating systems uses a minimal
kernel; most services run as user-level applications. Communication takes
place via message passing.
• A modular approach for designing operating systems provides operatingsystem services through modules that can be loaded and removed during
run time. Many contemporary operating systems are constructed as hybrid
systems using a combination of a monolithic kernel and modules.
• A boot loader loads an operating system into memory, performs initialization, and begins system execution.
• The performance of an operating system can be monitored using either
counters or tracing. Counters are a collection of system-wide or perprocess statistics, while tracing follows the execution of a program through
the operating system.

# ++

- 운영체제는 프로그램 실행을 위한 환경을 제공하며, 사용자와 프로그램에 다양한 서비스를 제공합니다.

- 운영체제와 상호작용하는 주요 접근 방식은 (1) 명령 인터프리터, (2) 그래픽 사용자 인터페이스, (3) 터치스크린 인터페이스의 세 가지입니다.
- 시스템 호출(System calls)은 운영체제가 제공하는 서비스에 대한 인터페이스를 제공합니다. 프로그래머는 시스템 호출의 응용 프로그래밍 인터페이스(API)를 사용하여 시스템 호출 서비스를 접근합니다.
- 시스템 호출은 다음의 여섯 가지 주요 범주로 나눌 수 있습니다: (1) 프로세스 제어, (2) 파일 관리, (3) 장치 관리, (4) 정보 유지, (5) 통신, (6) 보호.
- 표준 C 라이브러리는 UNIX 및 Linux 시스템을 위한 시스템 호출 인터페이스를 제공합니다.
- 운영체제는 사용자에게 유틸리티를 제공하는 시스템 프로그램의 모음도 포함합니다.
- 링커(Linker)는 여러 개의 재배치 가능한 오브젝트 모듈을 하나의 바이너리 실행 파일로 결합합니다. 로더(Loader)는 실행 파일을 메모리에 로드하여 사용 가능한 CPU에서 실행할 수 있도록 합니다.
- 애플리케이션이 운영체제 특정이 되는 이유는 여러 가지가 있습니다. 여기에는 프로그램 실행 파일의 다양한 바이너리 형식, 서로 다른 CPU의 서로 다른 명령어 집합, 그리고 운영체제마다 다른 시스템 호출이 포함됩니다.
- 운영체제는 특정 목표를 염두에 두고 설계됩니다. 이러한 목표는 궁극적으로 운영체제의 정책을 결정합니다. 운영체제는 이러한 정책을 특정 메커니즘을 통해 구현합니다.
- **모놀리식 운영체제(Monolithic Operating System)**는 구조가 없으며, 모든 기능이 단일 정적 바이너리 파일로 제공되어 단일 주소 공간에서 실행됩니다. 이러한 시스템은 수정하기 어려운 반면, 주요 장점은 효율성입니다.
- **계층화된 운영체제(Layered Operating System)**는 여러 개의 개별 계층으로 나뉘며, 가장 하위 계층은 하드웨어 인터페이스, 가장 높은 계층은 사용자 인터페이스입니다. 계층화된 소프트웨어 시스템은 어느 정도 성공을 거두었지만, 성능 문제로 인해 운영체제를 설계하는 데 일반적으로 이상적이지 않습니다.
- 마이크로커널(Microkernel) 접근법은 최소한의 커널을 사용하는 운영체제 설계를 특징으로 하며, 대부분의 서비스는 사용자 수준의 애플리케이션으로 실행됩니다. 통신은 메시지 전송을 통해 이루어집니다.
- 모듈화된 운영체제(Modular Operating System) 설계 접근법은 런타임 중에 로드하고 제거할 수 있는 모듈을 통해 운영체제 서비스를 제공합니다. 많은 현대 운영체제는 모놀리식 커널과 모듈의 조합을 사용하여 하이브리드 시스템으로 구성됩니다.
- **부트 로더(Boot Loader)**는 운영체제를 메모리에 로드하고 초기화를 수행한 후 시스템 실행을 시작합니다.
- 운영체제의 성능은 카운터 또는 추적(tracing)을 사용하여 모니터링할 수 있습니다. 카운터는 시스템 전체 또는 프로세스별 통계의 모음이며, 추적은 프로그램의 실행을 운영체제를 통해 따라갑니다.