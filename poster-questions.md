
## log20 
지원되는 언어가 뭐에요? 자바  
숙련된 개발자가 찍는 로그보다 더 좋나요? 네 (그래프 보여주면서) 시스템 복잡도가 증가할수록   
개발자 커스터마이징이 되니요? 그러니까 로그가 필요 앖는 경우 삭제가 가능한지?  네  
로그 종류 별 지원 되나요? 아뇨  
데모는 있나요?(그러니까 실제 프로그램이 찍는 로그를 보면 감이 올거 같아서) 지금 준비는 안 됬는데 메일보내주면 보여주겠다고 함  

## 펜시브
펜시브는 자바 바이트코드에 의존한다고 들었는데 그러면 c c++ 애플리케이션에서의 지원은 어떤가요?  
원리적으로 가능하기는 하는데 c c++은 프로그램은 가능한 상태 갯수가 자바보다 너무 많아서 매우 복잡함.   
(아마 타입 세이프한 특징이 많이 반영된 결과인듯) 즉 바이트코드에 특징적인 기능은 쓰지 않기 때문에 가능은 함..  

## io오토마타 mit
tla+도 같은 기능을 하는데 그것과의 차이점은 무엇잉가요?  
즉, 상태 머신과 그것들의 입 출력을 규명하고 안전성을 검증하는 것이 똑 같음? 우리는 코드 생성까지도 한다.  
자동 생성된 코드의 성능은? (체계적인 실험은) 안 해 보았다. 단순한 예제만 해보았다.  
언어는 무엇이 지원됩니까? 하스켈이요  
왜 하스켈이지요? 함수형 언어.. 등등 뭐라 했는데 기억 안남  

## 알고랜드 mit
알고랜드는 퍼블릭 블록체인 용으로 설계된 것 같은데 프라이빗 블록체인에서도 적용이 가능합니까? 네, 우리는 실제로 그렇게도 테스트를 해보았다  
그럴 경우 성능은 얼마나 향상이 되었나?  물론 참가자 수에 따라 다르겠지만 수십배 정도 난다  
전통적인 비잔틴 알고리즘과 많이 다르네요? 넹  

## 리눅스 커널의 분산 파일 패치
이 작업은 리눅스 커널 메인라인에 커밋이 되었습니까? (포스터에 젠투 로고를 보여주면서) 젠투 리눅스에 반영 되어 있습니다.  
신뢰된 제3자가(벤더) 요구되는데 이들을 블록체인을 사용해서 없애면 더 효과적일 것 같습니다? 네 그런것 같아요 ㅎㅎ  
(젠투 리눅스 명함을 받음)  

## 그래프 병렬 계산 : 한양대, 유니스트
그 hi?  
나 안녕하세요?  
그 아 한국분이군요 ㅎㅎ  
나 네 ㅎㅎ, (포스터를 좀 보다가) 그럼 이건 그래프를 병렬 처리하는 것과 관련이 있는거네요?  
그 그렇긴 하지만 주 포인트는 로드 밸런싱, 캐시 지역성을 활용한 ....   
(길게 설명 해주심)  


## 폴트 톨러런트한 액터 모델, 
나: 크래시 폴트만 지원이 됩니까?   
그: 무슨 말이시죠?  
나 음 arbitrary 폴트 같은 것도 톨러런트기 됩니까?  
그 (이해 못하겠다는 표정으로) 다시 말좀?  
나 그러미까 만약 일부 액터가 악의적인 행동을 하능 것도 감내가 됩니까? 즉 액터가 처음에 정해진 프로토콜에서 벗어난 행동을 하는 것에 어떻게 대응합니까?   
그 사용자가 액터를 정의하기 때문에 액터가 악의적인 행동을 한다고 보기는 어렵습니다.'우리는 보안과 괸련된 주제가 아니에요  

## tee를 사용한 프라이버시 보호
인텔은 sgx 임베디드 보드 지원이 안 되는데 어떻게 작은 기기에서 신뢰된 실행이 되나요? 작은 기기는 arm trust zone, sgx는 클라우드에서 동작한답니다 ^^  

## 64키로 바이트 메모리에서 안전하고 효율적으로 멀티프로그래밍하기
제가 직접 마이크로컨트롤러에 저 os를 설치할수 있습니까? 네, (포스터에 적힌 홈페이지를 가리키며) 저홈페이지에 들어가시면 소스가 공개되어 있습니다.   
그리고 기타 다양한 보드에 대한 지원이 가능하다고 언급(보드 종류를 많이 얘기함) cortex m4 뿐만 아니라,  
