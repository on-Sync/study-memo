### 1. Program vs Process vs Thread

#### Program
- A set of instructions of computer
- 컴퓨터 동작을 위한 명령묶음

#### Process
- Loaded program on memory
- 실행중인 프로그램

#### Thread
- A flow of action in process
- 프로세스 내부의 논리적 명령처리 단위

### 2. Thread :: Concurrency vs Parallelism

#### Concurrency
- CS 에서 동시성은 주로 시간의 일치보단 근접을 표현한다.
- Thread 처리의 동시성은 CPU Core 내부에서 Thread (논리적) 에 대한 Context switch 이 미세한 시간단위로 이루어 지기에 거의 동시에 수행된다고 보는 것이다.

#### Parallelism
- Concurrency 와는 다르게 정확히 동일한 시간에 수행되는 관련된 명령수행 방법을 말한다.
- Thread 처리의 병렬성은 CPU Core (물리적) 으로 별도의 Unit 을 사용하여 수행하는 것을 말한다.

### 3. Event loop 란?

...
