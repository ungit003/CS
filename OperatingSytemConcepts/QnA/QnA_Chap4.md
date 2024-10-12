# Chapter 4 Threads & Concurrency
- Identify the basic components of a thread, and contrast threads and processes.
- Describe the major benefits and significant challenges of designing multithreaded processes.
- Illustrate different approaches to implicit threading, including thread pools,
fork-join, and Grand Central Dispatch.
- Describe how the Windows and Linux operating systems represent threads.
- Design multithreaded applications using the Pthreads, Java, and Windows threading APIs.

# 1. Overview

# 2. Multicore Programming

# 3. Multithreading Models

# 4. Thread Libraries

# 5. Implicit Threading

# 6. Threading Issues

# 7. Operating-System Examples

# +
• A thread represents a basic unit of CPU utilization, and threads belonging
to the same process share many of the process resources, including code
and data.
• There are four primary benefits to multithreaded applications: (1) responsiveness, (2) resource sharing, (3) economy, and (4) scalability.
• Concurrency exists when multiple threads are making progress, whereas
parallelism exists when multiple threads are making progress simulta-
Practice Exercises 197
neously. On a system with a single CPU, only concurrency is possible;
parallelism requires a multicore system that provides multiple CPUs.
• There are several challenges in designing multithreaded applications.
They include dividing and balancing the work, dividing the data between
the different threads, and identifying any data dependencies. Finally, multithreaded programs are especially challenging to test and debug.
• Data parallelism distributes subsets of the same data across different computing cores and performs the same operation on each core. Task parallelism distributes not data but tasks across multiple cores. Each task is
running a unique operation.
• User applications create user-level threads, which must ultimately be
mapped to kernel threads to execute on a CPU. The many-to-one model
maps many user-level threads to one kernel thread. Other approaches
include the one-to-one and many-to-many models.
• A thread library provides an API for creating and managing threads. Three
common thread libraries include Windows, Pthreads, and Java threading.
Windows is for the Windows system only, while Pthreads is available for
POSIX-compatible systems such as UNIX, Linux, and macOS. Java threads
will run on any system that supports a Java virtual machine.
• Implicit threading involves identifying tasks—not threads—and allowing
languages or API frameworks to create and manage threads. There are
several approaches to implicit threading, including thread pools, fork-join
frameworks, and Grand Central Dispatch. Implicit threading is becoming
an increasingly common technique for programmers to use in developing
concurrent and parallel applications.
• Threads may be terminated using either asynchronous or deferred cancellation. Asynchronous cancellation stops a thread immediately, even if it
is in the middle of performing an update. Deferred cancellation informs
a thread that it should terminate but allows the thread to terminate in an
orderly fashion. In most circumstances, deferred cancellation is preferred
to asynchronous termination.
• Unlike many other operating systems, Linux does not distinguish between
processes and threads; instead, it refers to each as a task. The Linux
clone() system call can be used to create tasks that behave either more
like processes or more like threads.

# ++
스레드는 CPU 사용의 기본 단위를 나타내며, 동일한 프로세스에 속하는 스레드는 코드와 데이터 등 많은 프로세스 자원을 공유합니다.

다중 스레드 애플리케이션의 네 가지 주요 이점은 다음과 같습니다: (1) 반응성(responsiveness), (2) 자원 공유(resource sharing), (3) 경제성(economy), (4) 확장성(scalability).
**동시성(concurrency)**은 여러 스레드가 진행 중일 때 존재하며, **병렬성(parallelism)**은 여러 스레드가 동시에 진행 중일 때 존재합니다. 단일 CPU가 있는 시스템에서는 동시성만 가능하며, 병렬성을 위해서는 다중 코어 시스템이 필요합니다.
다중 스레드 애플리케이션 설계에는 여러 가지 도전 과제가 있습니다. 여기에는 작업을 나누고 균형을 맞추는 것, 서로 다른 스레드 간의 데이터를 나누는 것, 데이터 종속성을 식별하는 것이 포함됩니다. 마지막으로, 다중 스레드 프로그램은 특히 테스트와 디버깅이 어렵습니다.
**데이터 병렬성(data parallelism)**은 동일한 데이터의 하위 집합을 서로 다른 컴퓨팅 코어에 분산시키고 각 코어에서 동일한 작업을 수행합니다. **작업 병렬성(task parallelism)**은 데이터를 분산시키는 것이 아니라 여러 코어에 작업을 분배합니다. 각 작업은 고유한 작업을 실행합니다.
사용자 애플리케이션은 사용자 수준의 스레드를 생성하며, 이러한 스레드는 궁극적으로 CPU에서 실행하기 위해 커널 스레드에 매핑되어야 합니다. 다대일(many-to-one) 모델은 많은 사용자 수준 스레드를 하나의 커널 스레드에 매핑합니다. 다른 접근 방식에는 일대일(one-to-one) 및 다대다(many-to-many) 모델이 포함됩니다.
스레드 라이브러리는 스레드를 생성하고 관리하기 위한 API를 제공합니다. 세 가지 일반적인 스레드 라이브러리는 Windows, Pthreads, Java 스레딩입니다. Windows는 Windows 시스템 전용이며, Pthreads는 UNIX, Linux, macOS와 같은 POSIX 호환 시스템에서 사용할 수 있습니다. Java 스레드는 Java 가상 머신을 지원하는 모든 시스템에서 실행될 수 있습니다.
**암시적 스레딩(implicit threading)**은 스레드가 아닌 작업을 식별하고 언어 또는 API 프레임워크가 스레드를 생성하고 관리하도록 하는 방식입니다. 암시적 스레딩에는 스레드 풀, 포크-조인(fork-join) 프레임워크, 그랜드 센트럴 디스패치(Grand Central Dispatch) 등 여러 접근 방식이 있습니다. 암시적 스레딩은 동시 및 병렬 애플리케이션 개발에서 프로그래머가 사용하는 점점 더 일반적인 기술이 되고 있습니다.
스레드는 비동기적(asynchronous) 또는 지연적(deferred) 취소를 통해 종료될 수 있습니다. 비동기적 취소는 스레드가 업데이트를 수행하는 중에도 즉시 종료됩니다. 지연적 취소는 스레드에게 종료해야 함을 알리지만, 스레드가 질서 있게 종료될 수 있도록 허용합니다. 대부분의 경우, 지연적 취소가 비동기적 종료보다 선호됩니다.
많은 다른 운영체제와 달리, 리눅스는 프로세스와 스레드를 구분하지 않고 이를 모두 **작업(task)**이라고 부릅니다. 리눅스의 clone() 시스템 호출을 사용하면 프로세스처럼 또는 스레드처럼 동작하는 작업을 생성할 수 있습니다.