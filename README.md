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

### WatchIT: Who Watches Your IT Guys? (누가 IT 직원을 감시할것인가?)
#### 문제: 회사에서 IT 관리자 업무 보는 직원은 회사의 모든 자원에 접근할 수 있는데, 이들이 악의적인 행동을 하는지 어떻게 감시할것인가?
#### 해결: IT 관리자가 문제 해결에 충분한 정보는 제공하되, 정도를 벗어난 행동에 대해서는 제약을 가하는(감시) 수단을 개발(WatchIT)
- 구멍이 송송 뚫린 컨테이너(perforated container): 기존의 리눅스 컨테이너는 너무나 제약이 많아서 IT 관리자 입장에서는 문제 해결하기가 너무 힘듬. 그래서 그러한 제약을 좀 덜어낸 컨테이너가 필요. 즉, 최소 권한의 원칙을 따른 컨테이너.
- 그러니까 리눅스 컨테이너보다 좀 덜한 isolation 환경을 제공하는거지. 딱 문제 해결에 필요한 정보만 접근할수있도록.
- 근데, 문제가 주어진 컨테이너의 제약을 벗어나도록 요구한다면? 
    - 허용한다. 하지만 컨테이너 바깥의 활동은 로깅이 되기 때문에 이상한 행동을 하면 걸림


### Scaling a file system to many cores using an operation log(동작 로그를 사용해서 파일 시스템이 다수의 코어를 사용하도록 확장시키기)

#### 문제: 멀티 코어를 활용해서 파일 시스템 효율성 개선시키기, 그리고 멀티 코어의 전형적인 동기화 문제
파일 시스템 실행 효율을 멀티코어를 사용해서 개선시키고  캐시-메인메모리-디스크 간의 동기화를 효율적으로 하는 방법이 뭘까? 

#### 해결: scaleFS, CPU 별 동작 로그를 사용해서 디스크 안의 파일 시스템과 메모리 안의 파일 시스템을 분리시킴(근데 언젠가는 합쳐야한다는)
그러니까 코어 별로 파일 시스템의 동작을 나눠서 캐시 충돌을 줄이겠다는 소리아닌가? 대신에 각 코어 별로 진행한 사항들을 합칠때(fsync 호출시) 정확하고 빠르게 합쳐야한다는 요구 사항이 생기게 됨.

### Stadium: A Distributed Metadata-Private Messaging System (메타데이터의 비밀성을 유지하는 분산 메시징 시스템)
#### 문제: 인터넷 환경에서 비밀 통신(private communication)할때의 발생하는 문제들 해결하기
1. 메시지를 암호화해도 누가 누구에게 보내느냐와 같은 정보(메타데이터)는 traffic analysis 공격때문에 노출될 수 있음(이미 제안된 솔루션, Vuvuzela)
2. 메타데이터의 비밀성을 유지하는 대규모 시스템은 모든 메시지를 적은 수의 제공자(provider)에게 넘겨줄 것을 요구하기 때문에 각 제공자의 부담이 크고, 이는 실용성을 떨어뜨리는 주범임 --> 제공자의 부담을 덜어주는 테크닉이 필요

#### 해결: 데이터와 메타데이터의 비밀성을 유지하면서 제공자의 계산 부담을 덜어주는 메시징 시스템 개발
- 분산 노이즈 생성(distributed noise generation)?
- 비밀성이 있는 데이터는 특이하게 라우팅하기(differentially private routing): 프라이빗 데이터는 라우팅 방법을 서로 다르게 한다?
- 검증가능한 병렬 믹스넷(verifiable parallel mixnet): 추적하기 매우 힘든 통신 프로토콜(믹스넷)을 병렬로 만들고 이를 검증가능하게 함.각 서버들은 협력해서 다른 서버들이 해당 프로토콜을 잘 수행하고있는지 검사하게 함.

#### 의문
1. 제공자(provider)의 계산량을 어떻게 줄여준다는거지? 요약에 나와 있는 정보만으로는 알아내기가 힘듬.


### Atom: Horizontally Scaling Strong Anonymity (수평적으로 확장가능한 강력한 익명성)
#### 문제: Atom의 아키텍처는 이론적으로는 잘 정립이 되어 있지만 이를 현실 세계에서 실용적인 솔루션으로 변모시키기 위해서 필요한 테크닉은 무엇인가?
Atom의 아키텍처는 traffic analysis 공격에 대응하는 구조임. 아톰 서버는 전체 메시지 중 아주 조금만 보기 때문에 통신 부담이 적고 이는 확장성의 증대로 이어짐. 그리고 사용자의 익명성 보장에도(확률적으로?) 효율적임.(서버 X가 사용자 A의 메시지를 못볼 가능성이 크기 때문에) 여기까지는 기존에 있던 얘기. 이를 현실에서 쓸만한 소프트웨어로 만들기 위해서 넘어야 하는 벽이 많음. 이를 극복하는 방법에 초점이 맞춰져 있음.

#### 해결
1. 계산량이 많은 제3자 프로토콜들을 많이 사용하지 않기
2. 최소한의 비용으로 적극적이고 악의적인 서버의 공격을 방어해내기
3. 서버 고장, churn(?, 아마 여러 대의 서버 고장을 혼란스럽다고 표현한 듯) 다루기

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


