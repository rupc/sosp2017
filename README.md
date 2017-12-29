# sosp2017

SOSP2017 은 50년 역사상 최초 기록을 몇개 세움:

* SOSP 2017은 최초로 북아메리카와 유럽 대륙 이외의 곳에서 열리는 행사임.
* 233개의 제출된 논문 중, 39개의 논문이 최종 승인되었는데\(39/233 = 16.7% acceptance ratio\), 이는 SOSP 역사상 최대 수치임

## 분야

* kernels  
  * NEVE: Nested Virtualization Extensions for ARM 
  * My VM is Lighter \(and Safer\) than your Container
  * Multiprogramming a 64kB Computer Safely and Efficiently
* storage systems  
* privacy and security \(miguel castro\)  
  * WatchIT: Who Watches Your IT Guy?
  * The Efficient Server Audit Problem, Deduplicated Re-execution, and the Web
  * Secure Page Fusion with VUsion
* understanding and fixing bugs
  * DeepXplore: Automated Whitebox Testing of Deep Learning Systems
  * Pensieve: Non-Intrusive Failure Reproduction for Distributed Systems using the Event Chaining Approach
  * Canopy: An End-to-End Performance Tracing And Analysis System
* in-network computing
  * Eris: Coordination-Free Consistent Transactions Using In-Network Concurrency Control
  * NetCache: Balancing Key-Value Stores with Fast In-Network Caching
  * KV-Direct: High-Performance In-Memory Key-Value Store with Programmable NIC
* scalability 
  * Algorand: Scaling Byzantine Agreements for Cryptocurrencies
  * Scaling a file system to many cores using an operation log
  * SVE: Distributed Video Processing at Facebook Scale
* resource management
  * Resource Central: Understanding and Predicting Workloads for Improved Resource
  * MittOS: Supporting Millisecond Tail Tolerance with Fast Rejecting SLO-Aware OS Interface
  * Monotasks: Architecting for Performance Clarity in Data Analytics Frameworks
    Management in Large Cloud Platforms
* Understanding failures
  * Log20: Fully Automated Optimal Placement of Log Printing Statements under Specified Overhead Threshold
  * Lazy Diagnosis of In-Production Concurrency Bugs
  * CrystalNet: Faithfully Emulating Large Production Networks
* verification
  * Komodo: Using verification to disentangle secure-enclave hardware from software
* Data analytics
* Adaptation and repair

## Paper abstract

### Canopy: An End-to-End Performance Tracing And Analysis System

Canopy\(이하, 캐노피\)는 페이스 북에서 개발한 성능 분석 도구이다. 캐노피는 클라이언트의 요청을 받는 지점에서부터 요청이 처리된 후 완료되기까지의 과정\(end-to-end\)을 추적하고 데이터를 만들어내고 이들 데이터를 분석한다. 클라이언트는 웹 브라우저, 모바일 애플리케이션, 백엔드 서버를 포함한다. 단순히 네트워크 관련 성능 분석 도구라면 별 다른 메리트가 없겠지만 캐노피는 다음과 같은 점에서 기존 성능 분석 도구들과의 차이를 보인다.

* 실시간 분석
* 대규모 분석: 10억개 이상의 사용자 요청을 취합한 데이터를 생성하고 분석
* 사용자 별 기능\(user specific feature\) 분석  

실시간 분석은 서버 상에 코드가 업데이트가 되었다거나, 설정을 바꾼다거나 하는 상황에서도 적용된다. 그리고 다양한 장치, 다양한 사용자들이 만들어내는 다양한 요청, 다양한 데이터 센터 서버들과 같이 이질적인 환경을 가정하기 때문에 각 상황마다 서로 다른 성능 측정 메트릭이 필요하다. 하나의 일관된 메트릭만으로는 모든 이질적인 상황을 일관되게 표현하는 것은 그다지 깔끔하지 못하다고 보기 때문이다.

캐노피도 물론 기존에 잘 만들어진 성능 분석 도구를 아예 안 쓰지는 않았다. X-Trace: A Pervasive Network Tracing Framework\(NSDI 2007\), Dapper: a Large-Scale Distributed Systems Tracing Infrastructure\(Google Tech report, 2010\) 를 핵심 엔진으로 사용하고 있다.

정리해서, 캐노피가 해결하려는 3가지 주요 문제는 다음과 같다.

1. 이질적인 환경에서의 성능 분석\(다양한 실행 환경, 데이터 품질, 소프트웨어 스택의 각 계층\)
2. 고수준 분석에서부터 저수준 분석을 아우르는 분석
3. 엔지니어에게 필요한 데이터만 제공하기\(일반적인 인터페이스 뿐만 아니라, 엔지니어 맞춤형\(customization\) 데이터만 추출해서 제공하는 인터페이스 제공\) 

캐노피는 이 문제들을 해결하기 위해 완전한 파이프라인을 제공한다. 파이프라인은 유닉스의 전통적인 개념과 유사하다. 클라이언트의 요청의 각 처리 단계를 파이프라인으로 추상화하고, 각 단계는 측정하려고하는 대상에 맞춤화\(customization\)된 설계가 적용되고, 독립적으로 수정가능하다. 캐노피는 특히 이러한 파이프라인 각 단계의 맞춤화를 강조한다. 이는 개발 시점에서 실행 모델에 따라 맞춤화된\(tailored\) API 를 사용하였다. 런타임 중에는 성능 데이터를 이벤트 기반의 표현 형식에 맞추어 생성된다.

### SVE: Distributed Video Processing at Facebook Scale

### 

### NetCache: Balancing Key-Value Stores with Fast In-Network Caching

### Resource Central: Understanding and Predicting Workloads for Improved Resource Management in Large Cloud Platforms

### MittOS: Supporting Millisecond Tail Tolerance with Fast Rejecting SLO-Aware OS Interface KV-Direct: High-Performance In-Memory Key-Value Store with Programmable NIC

### Monotasks: Architecting for Performance Clarity in Data Analytics Frameworks

### NEVE: Nested Virtualization Extensions for ARM

### Eris: Coordination-Free Consistent Transactions Using In-Network Concurrency Control \(Eris: 내부 네트워크의 병행성 제어를 사용한 합의 없는 일관된 트랜잭션 처리 시스템\)

본 논문에서 제시된 Eris는 병행성 제어를 사용하여 합의 없이 일관성을 유지하는 트랜잭션 기 법을 제시한다. 오늘 날의 많은 웹 서비스와 애플리케이션들은 분산 스토리지 시스템에 많이 의 존한다. 분산 스토리지에서 일어나는 많은 작업은 데이터를 분산 시켜 놓는 작업, 그리고 분산 된 저장소들 사이의 일관성을 유지하는 것과 관련된다. 이를 소위 합의\(consensus\) 또는 협의 \(coordination\) 라고 부르는데, 이 과정은 많은 통신을 유발한다. Eris 는 트랜잭션들 사이의 독립 성\(independence\)를 고려하여, 정상 동작 과정\(normal case operation\)에서의 합의를 제거하여 트 랜잭션 처리 성능을 향상 시킨 트랜잭션 프로토콜이다. 이를 지원하기 위해 Eris는 네트워크 내 부의 병행성 제어\(In network concurrency control\) 기능을 사용한다.

이는 다음과 같은 기술적 목표를 가진다.

* 여러 목적지 데이터 센터에 전달된 메시지들에 대하여 전역적인 순서 정렬\(globally consistent ordering\)을 제공

  * 메시지 전달은 손실될 수 있음
  * 수신자는 손실된 메시지를 탐지할 수 있음

  따라서 병행성 제어의 뜻은 다수의 목적지에 도착한 메시지들을 서로 같은 순서로 처리하기 위 한 순서 정렬\(ordering\) 기능을 나타낸다. 전통적인 합의 알고리즘의 관점에서 설명하면, 클라이 언트는 단일한 프라이머리 노드에게 메시지를 전달하고 나면 이후의 과정은 프라이머리와 나 머지 리플리카 노드들 사이의 합의가 일어나지만, Eris에서는 클라이언트는 프라이머리 역할을 하는 노드 뿐만 아니라 서로 다른 노드들에 메시지를 전송할 수 있다. 사실 이러한 방식이 상태 머신 복제\(state mahcine replication\)의 기본적인 테크닉이기도 하다. Eris는 또한 시퀀서 \(sequencer\)라는 특별한 노드를 설정하는데 이 노드의 역할은 전통적인 SMR 프로토콜에서 프 라이머리 노드와 유사하다.

Eris는 노드들을 그룹핑 시켜 멀티캐스트 메시지의 수신 노드들을 정해둔다. 그리고 시퀀서 \(sequencer\) 노드는 각 그룹 별 카운터를 관리한다. 노드들을 그룹핑 시키는 이유는 각 트랜잭션 별 담당하는 노드 그룹을 형성하여 독립적인 트랜잭션은 합의 없이 처리하기 위함이다.

### The Efficient Server Audit Problem, Deduplicated Re-execution, and the Web \(서버 감독을 효율적으로 하는 방법, 중복이 제거된 재-실행, 그리고 웹\)

#### 문제: 서버에 업로드한 내 프로그램이 제대로 실행되는지 어떻게 신뢰할 수 있겠는가?\(특히 concurrent feature를 많이 사용하는 program일때\)

전통적인 secure remote computation 문제. 내가 내 프로그램짜서 서버에 업로드하고, 서버가 내 프로그램을 실행시켰다고 하자. 내 프로그램은 이러저러한 상황에서 이러저러한 로그를 찍도록 되어 있다. 서버는 프로그램을 실행시키면서 생성된 로그를 나에게 보내준다. 나는 이를 곧이곧대로 믿을 것인가? 서버가 올바르다면야, 문제가 안 되겠지만 서버가 의도적으로 로그를 조작할 수도 있지 않는가? 또는 동시성 프로그래밍때문에 의도치 않은 에러가 발생할 수도 있지 않을까? 논문에서는 이 문제를 Efficient Server Audit Problem으로 규정.

#### 해결: 동시다발적인 재실행\(simultaneous replay\), 동시성 실행의 효율적인 검증\(efficient verification of concurrent executions\)

### DeepXplore: Automated Whitebox Testing of Deep Learning Systems \(딥 러닝 시스템을 위한 화이트 박스 테스팅의 자동화\)

#### 문제: 기존의 딥러닝 테스트 케이스는 사람이 일일히 수작업으로 하나씩 데이터에 라벨링을 해주었는데\(감독 학습인 경우\), 시스템이 복잡해지면서 이 방식에 한계가 생김\(특히, corner case \). 인간이 이해하기 무지막지하게 어려운 복잡한 딥러닝 시스템은 어떻게 테스팅 할 것인가?

#### 해결: DeepXplore 을 제안

DL의 구성 요소에 대한 테스트 케이스를 자동 생성해주는 툴. 특히 corner case를 잘 찾아줌. 구체적으로는 neuron coverage 개념을 도입하고 이를 측정: neuron coverage는 뉴럴 네트웍 상에서의 테스트 되는 뉴런의 경로를 의미. 그리고 자동 생성된 테스트 케이스를 가지고 같은 딥러닝 시스템을 다시 훈련시키면 model accuacy가 3% 올라간다는 것을 보여줌

### Multiprogramming a 64 kB Computer Safely and Efficiently

#### 문제: 저전력, 빈약한 하드웨어 지원을 갖는 컴퓨터에 어떻게 안전하고 효율적으로 멀티프로그래밍 기법을 제공할 것인가?

저전력 마이크로컨트롤러들은 여러 프로세스들을 메모리에 올려서 실행하는 멀티프로그래밍 기법을 지원을 잘 하지 못한다. 왜냐하면 하드웨어 기반의 지원이 빈약하기 때문. 하지만, 임베디드 컴퓨팅의 전통적인 특수 목적\(special purpose\) 애플리케이션보다는 다양한 프로그램을 돌릴 수 있게 해주는 소프트웨어 플랫폼 개발이 중요해지고 있음.

#### 해결: Tock OS를 제시

Tock는

* 저전력 플랫폼 지원
* 제한된 하드웨어 보호 기능들의 이점들을 최대한 활용
* Rust 프로그래밍 언어의 type-safe 기능 활용
* 소프트웨어 오류를 고립시킴
* 메모리 보호 제공
* 동적 메모리 관리를 효율적으로 수행 

### My VM is Lighter \(and Safer\) than your Container \(내 가상 머신은 당신의 컨테이너보다 더 빠르고 안전하다\)

#### 문제: 가상머신의 강한 고립성은 유지하면서 성능은 컨테이너 수준으로 끌어내릴 수 없을까?

컨테이너가 가볍고 빠르고 인기도 많은데, 어떤 사람들은 가상 머신안에서 컨테이너를 돌린다. 왜 그럴까? 컨테이너는 가상머신보다 고립성\(isolation\) 지원이 더 약하기 때문이다.

즉, 가상머신의 강한 고립성과 컨테이너의 효율성 사이의 성능 trade-off 가 있는 셈이다.

이 논문은 이러한 trade-off를 실제로 상세하게 조사해서 가상 머신의 고립성은 유지한채로 효율성은 컨테이너보다 더 높게 나올 수 있다고 주장한다.

#### 해결: 경량 VM\(LightVM\)을 제시

LightVM은

* 특수 목적 애플리케이션 지원을 위해 unikernel을 사용
* Xen 기반의 가상화 솔루션
* 빠른 boot-up 을 지원 \(현재 실행중인 VM 갯수에 상관없이\)
* Xen의 컨트롤 플레인을 재설계하여, 집중식 연산을 분산된 연산으로 변환\(하이퍼바이저와의 상호작용을 최소한으로 줄임\)

### WatchIT: Who Watches Your IT Guys? \(누가 IT 직원을 감시할것인가?\)

#### 문제: 회사에서 IT 관리자 업무 보는 직원은 회사의 모든 자원에 접근할 수 있는데, 이들이 요구된 문제 해결 이외의 악의적인 행동을 하는지 어떻게 감시할것인가?

#### 해결: IT 관리자가 문제 해결에 충분한 정보는 제공하되, 정도를 벗어난 행동에 대해서는 제약을 가하는\(감시\) 수단을 개발\(WatchIT\)

* 구멍이 송송 뚫린 컨테이너\(perforated container\): 기존의 리눅스 컨테이너는 너무나 제약이 많아서 IT 관리자 입장에서는 문제 해결하기가 너무 힘듬. 그래서 그러한 제약을 좀 덜어낸 컨테이너가 필요. 즉, 최소 권한의 원칙을 따른 컨테이너.
* 그러니까 리눅스 컨테이너보다 좀 덜한 isolation 환경을 제공하는거지. 딱 문제 해결에 필요한 정보만 접근할수있도록.
* 근데, 문제가 주어진 컨테이너의 제약을 벗어나도록 요구한다면? 
  * 허용한다. 하지만 컨테이너 바깥의 활동은 로깅이 되기 때문에 이상한 행동을 하면 걸림

### Scaling a file system to many cores using an operation log\(동작 로그를 사용해서 파일 시스템이 다수의 코어를 사용하도록 확장시키기\)

#### 문제: 멀티 코어를 활용해서 파일 시스템 효율성 개선시키기, 그리고 멀티 코어의 전형적인 동기화 문제

파일 시스템 실행 효율을 멀티코어를 사용해서 개선시키고  캐시-메인메모리-디스크 간의 동기화를 효율적으로 하는 방법이 뭘까?

#### 해결: scaleFS, CPU 별 동작 로그를 사용해서 디스크 안의 파일 시스템과 메모리 안의 파일 시스템을 분리시킴\(근데 언젠가는 합쳐야한다는\)

그러니까 코어 별로 파일 시스템의 동작을 나눠서 캐시 충돌을 줄이겠다는 소리아닌가? 대신에 각 코어 별로 진행한 사항들을 합칠때\(fsync 호출시\) 정확하고 빠르게 합쳐야한다는 요구 사항이 생기게 됨.

### Stadium: A Distributed Metadata-Private Messaging System \(메타데이터의 비밀성을 유지하는 분산 메시징 시스템\)

#### 문제: 인터넷 환경에서 비밀 통신\(private communication\)할때의 발생하는 문제들 해결하기

1. 메시지를 암호화해도 누가 누구에게 보내느냐와 같은 정보\(메타데이터\)는 traffic analysis 공격때문에 노출될 수 있음\(이미 제안된 솔루션, Vuvuzela\)
2. 메타데이터의 비밀성을 유지하는 대규모 시스템은 모든 메시지를 적은 수의 제공자\(provider\)에게 넘겨줄 것을 요구하기 때문에 각 제공자의 부담이 크고, 이는 실용성을 떨어뜨리는 주범임 --&gt; 제공자의 부담을 덜어주는 테크닉이 필요

#### 해결: 데이터와 메타데이터의 비밀성을 유지하면서 제공자의 계산 부담을 덜어주는 메시징 시스템 개발

* 분산 노이즈 생성\(distributed noise generation\)?
* 비밀성이 있는 데이터는 특이하게 라우팅하기\(differentially private routing\): 프라이빗 데이터는 라우팅 방법을 서로 다르게 한다?
* 검증가능한 병렬 믹스넷\(verifiable parallel mixnet\): 추적하기 매우 힘든 통신 프로토콜\(믹스넷\)을 병렬로 만들고 이를 검증가능하게 함.각 서버들은 협력해서 다른 서버들이 해당 프로토콜을 잘 수행하고있는지 검사하게 함.

#### 의문

1. 제공자\(provider\)의 계산량을 어떻게 줄여준다는거지? 요약에 나와 있는 정보만으로는 알아내기가 힘듬.

### Atom: Horizontally Scaling Strong Anonymity \(수평적으로 확장가능한 강력한 익명성\)

#### 문제: Atom의 아키텍처는 이론적으로는 잘 정립이 되어 있지만 이를 현실 세계에서 실용적인 솔루션으로 변모시키기 위해서 필요한 테크닉은 무엇인가?

Atom의 아키텍처는 traffic analysis 공격에 대응하는 구조임. 아톰 서버는 전체 메시지 중 아주 조금만 보기 때문에 통신 부담이 적고 이는 확장성의 증대로 이어짐. 그리고 사용자의 익명성 보장에도\(확률적으로?\) 효율적임.\(서버 X가 사용자 A의 메시지를 못볼 가능성이 크기 때문에\) 여기까지는 기존에 있던 얘기. 이를 현실에서 쓸만한 소프트웨어로 만들기 위해서 넘어야 하는 벽이 많음. 이를 극복하는 방법에 초점이 맞춰져 있음.

#### 해결

1. 계산량이 많은 제3자 프로토콜들을 많이 사용하지 않기
2. 최소한의 비용으로 적극적이고 악의적인 서버의 공격을 방어해내기
3. 서버 고장, churn\(?, 아마 여러 대의 서버 고장을 혼란스럽다고 표현한 듯\) 다루기

### Pensieve: Non-Intrusive Failure Reproduction for Distirbuted Systems using Event Chaining Approach \(이벤트 체이닝 접근법을 사용한, 그리고 분산 시스템을 위한 비-침투적인 고장 재생산 테크닉\)

#### 문제: 분산 시스템에서 에러 찾고 고치기가 매우 빡심... 즉 버그 재현을 하기가 매우 힘든데 이를 어떻게 커버할 것이냐?

분산 시스템 개발자의 manual guesswork 만으로는\(보통 printf문으로 찍힌 로그를 통해 추론하는\) 현실적으로 현대의 매우 복잡한 분산 시스템 소프트웨어 개발 부담을 감당하기가 매우 힘듬.\(넘나 복잡한 상황\)  
물론 기존의 버그 재현 테크닉이 있기는 하나 비효율적\(symbolic 실행은 전체 탐색을 통해 버그를 찾음\)

#### 해결: 관련된 놈만 추적

기존의 symbolic 실행은 버그 재현을 위해 버그에 이르는 모든 경로를 검색했지만, Pensieve는 Partial Trace Observation

* 펜시브는 인과적으로 의존적인 이벤트들간의 연결 고리를 추론하는 나름의 규칙을 갖고 있는데 이를 바탕으로 버그를 추적해냄. 
* 즉, 무식하게 brute-force로 찾지 않고, 관련성이 있는 것만 추적하겠다는 접근인데... 어떻게 보면 너무 당연

### Komodo: Using verification to disentangle secure-enclave hardware from software \(enclave 하드웨어를 소프트웨어로부터 분리시키기 위한 검증 기술\)

#### 문제: Intel SGX은 강력한 보안 기능\(isolation\)을 제공하기 위해 x86 아키텍처를 복잡하게 만들었음 --&gt; \(HW, SW의 의존관계가 복잡하여 유연성이 떨어짐\)

\(마이크로 커널이 초기에 단순함을 추구하였지만 이후 복잡해진 것처럼\)  
    : 이해하기 매우 힘들게 실리콘을 배치하고 마이크로 코드를 짬.

* 하드웨어 기반의 보안\(hardware based security\): 일반적으로 순수 소프트웨어보다 더 나은 성능 제공, 순수 소프트웨어가 제공하지 못하는 기능 제공. 
* 하드웨어 보안\(hardware only security\): 유연성이 떨어짐. 결함이 발견되었을때 혹은 새기능을 추가하고 싶을때, 업데이트 하기가 매우 힘듬. 여기서 Intel SGX의 단점이 제시됨. 그리고 이점을 노린게 Komodo임. 즉, enclave 하드웨어 기능 따로, 소프트웨어 따로 구성해서 유연성 높이자는 전략. \(구체적으로는 어떤식인지는 아직 깜깜무소식\)

  #### 해결: Komodo를 만듬

  * Komodo는 고립 실행 환경을 제공함. 그리고 다음과 같은 특징이 있음

* attested

* on-demand

* user-mode 
* concurrent
  * Komodo는 Intel SGX 보다 더 낫다?  \(어떤 면에서?\)
* enclave의 모든 기능을 제공.
* 모니터라고 하는 특권 소프트웨어가 enclave 기능을 구현.
* **CPU 업그레이드와 독립적인 enclave 기능 제공 가능**
* ARM trusted Zone 기반의 어셈블리 코드로 프로토타잎을 만들어서 개념 검증

#### 의문

1. Intel SGX의 복잡성을 문제로 지적했으면 그에 대응하는 단순성이 강조된 설명이 있어야 자연스러운데 요약문으로는 어떤식으로 단순화가 성취되었는지 불분명...

2. Intel SGX 보다 더 낫다고 했으니까, Intel SGX의 일부 기능을 보완하거나 대체하는 기술이 아니라 새로운 방식의 Isolation execution  
   을 제공하는 것인데... 그럴려면 결국 논문에서 제시된 특징 보다 더 복잡한 구현이 나오게 되지 않을까?



