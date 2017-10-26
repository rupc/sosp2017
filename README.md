# sosp2017
SOSP2017 은 50년 역사상 최초 기록을 몇개 세움:
 - SOSP 2017은 최초로 북아메리카와 유럽 대륙 이외의 곳에서 열리는 행사임.
 - 233개의 제출된 논문 중, 39개의 논문이 최종 승인되었는데(39/233 = 16.7% acceptance ratio), 이는 SOSP 역사상 최대 수치임

## 관심리스트
 - Bug hunting(Pensieve)
 - Understanding failures(Log20, Lazy Diagnosis of In-Production Concurrency Bugs, CrystalNet)
 - Security(WatchIT)
 - Privacy( **Stadium:A Distributed Metadata-Private Messaging System**)
 - Resource management(Resource Central, MittOS:SLO, Monotasks)
 - Scalability(**Algorand**)
 - Verification(Komodo: Using verification to disentangle secure-enclave hardware from software)

## 분야
 - kernels  
    - NEVE: Nested Virtualization Extensions for ARM 
    - My VM is Lighter (and Safer) than your Container
    - Multiprogramming a 64kB Computer Safely and Efficiently
 - storage systems  
 - privacy and security (miguel castro)  
    - WatchIT: Who Watches Your IT Guy?
    - The Efficient Server Audit Problem, Deduplicated Re-execution, and the Web
    - Secure Page Fusion with VUsion
 - understanding and fixing bugs
    - DeepXplore: Automated Whitebox Testing of Deep Learning Systems
    - Pensieve: Non-Intrusive Failure Reproduction for Distributed Systems using the Event Chaining Approach
    - Canopy: An End-to-End Performance Tracing And Analysis System
 - in-network computing
    - Eris: Coordination-Free Consistent Transactions Using In-Network Concurrency Control
    - NetCache: Balancing Key-Value Stores with Fast In-Network Caching
    - KV-Direct: High-Performance In-Memory Key-Value Store with Programmable NIC
 - scalability 
    - Algorand: Scaling Byzantine Agreements for Cryptocurrencies
    - Scaling a file system to many cores using an operation log
    - SVE: Distributed Video Processing at Facebook Scale
 - resource management
    - Resource Central: Understanding and Predicting Workloads for Improved Resource
    - MittOS: Supporting Millisecond Tail Tolerance with Fast Rejecting SLO-Aware OS Interface
    - Monotasks: Architecting for Performance Clarity in Data Analytics Frameworks
Management in Large Cloud Platforms
 - Understanding failures
    - Log20: Fully Automated Optimal Placement of Log Printing Statements under Specified Overhead Threshold
    - Lazy Diagnosis of In-Production Concurrency Bugs
    - CrystalNet: Faithfully Emulating Large Production Networks
 - verification
    - Komodo: Using verification to disentangle secure-enclave hardware from software
 - Data analytics
 - Adaptation and repair

## Paper abstract
### Pensieve: Non-Intrusive Failure Reproduction for Distirbuted Systems using Event Chaining Approach (이벤트 체이닝 접근법을 사용한, 그리고 분산 시스템을 위한 비-침투적인 고장 재생산 테크닉)
#### 문제: 분산 시스템에서 에러 찾고 고치기가 매우 빡심... 즉 버그 재현을 하기가 매우 힘든데 이를 어떻게 커버할 것이냐?
분산 시스템 개발자의 manual guesswork 만으로는(보통 printf문으로 찍힌 로그를 통해 추론하는) 현실적으로 현대의 매우 복잡한 분산 시스템 소프트웨어 개발 부담을 감당하기가 매우 힘듬.(넘나 복잡한 상황)
물론 기존의 버그 재현 테크닉이 있기는 하나 비효율적(symbolic 실행은 전체 탐색을 통해 버그를 찾음)
#### 해결: 관련된 놈만 추적
기존의 symbolic 실행은 버그 재현을 위해 버그에 이르는 모든 경로를 검색했지만, Pensieve는 Partial Trace Observation
- 펜시브는 인과적으로 의존적인 이벤트들간의 연결 고리를 추론하는 나름의 규칙을 갖고 있는데 이를 바탕으로 버그를 추적해냄. 
- 즉, 무식하게 brute-force로 찾지 않고, 관련성이 있는 것만 추적하겠다는 접근인데... 어떻게 보면 너무 당연


### Komodo: Using verification to disentangle secure-enclave hardware from software (enclave 하드웨어를 소프트웨어로부터 분리시키기 위한 검증 기술)
#### 문제: Intel SGX은 강력한 보안 기능(isolation)을 제공하기 위해 x86 아키텍처를 복잡하게 만들었음 --> (HW, SW의 의존관계가 복잡하여 유연성이 떨어짐)
(마이크로 커널이 초기에 단순함을 추구하였지만 이후 복잡해진 것처럼)
    : 이해하기 매우 힘들게 실리콘을 배치하고 마이크로 코드를 짬.
    - 하드웨어 기반의 보안(hardware based security): 일반적으로 순수 소프트웨어보다 더 나은 성능 제공, 순수 소프트웨어가 제공하지 못하는 기능 제공. 
    - 하드웨어 보안(hardware only security): 유연성이 떨어짐. 결함이 발견되었을때 혹은 새기능을 추가하고 싶을때, 업데이트 하기가 매우 힘듬. 여기서 Intel SGX의 단점이 제시됨. 그리고 이점을 노린게 Komodo임. 즉, enclave 하드웨어 기능 따로, 소프트웨어 따로 구성해서 유연성 높이자는 전략. (구체적으로는 어떤식인지는 아직 깜깜무소식)
#### 해결: Komodo를 만듬
 - Komodo는 고립 실행 환경을 제공함. 그리고 다음과 같은 특징이 있음
    - attested
    - on-demand
    - user-mode 
    - concurrent
 - Komodo는 Intel SGX 보다 더 낫다?  (어떤 면에서?)
    - enclave의 모든 기능을 제공.
    - 모니터라고 하는 특권 소프트웨어가 enclave 기능을 구현.
    - **CPU 업그레이드와 독립적인 enclave 기능 제공 가능**
    - ARM trusted Zone 기반의 어셈블리 코드로 프로토타잎을 만들어서 개념 검증

#### 의문
1. Intel SGX의 복잡성을 문제로 지적했으면 그에 대응하는 단순성이 강조된 설명이 있어야 자연스러운데 요약문으로는 어떤식으로 단순화가 성취되었는지 불분명...

2. Intel SGX 보다 더 낫다고 했으니까, Intel SGX의 일부 기능을 보완하거나 대체하는 기술이 아니라 새로운 방식의 Isolation execution 
을 제공하는 것인데... 그럴려면 결국 논문에서 제시된 특징 보다 더 복잡한 구현이 나오게 되지 않을까?


