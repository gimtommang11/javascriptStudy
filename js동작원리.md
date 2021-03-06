# js 동작원리
## 싱글스래드/멀티스래드
* ### 스래드란?
    * 프로그래밍이 시작될 때 동작이 구분되는 흐름
    * 수에 따라서 싱글스래드와 멀티스래드로 나뉨

* #### 싱글스래드와 멀티스레드
    * ex) 두 개의 작업을 하나의 스레드로 처리/ 2개의 스래드로 처리
    * 단순cpu만 이용->싱글스레드 좋음 / cpu이외 자원->멀티스레드 효율적

    * 싱글스레드
        - 한 작업을 마친 뒤,다른 작업 실행
    * 멀티스레드
        - 번갈아가며 작업 수행,동시에 두 작업이 처리되는것같은 느낌
        - 오히려 더 느릴수가 있다
            - 문맥 교환이 일어나기 때문
                - 실행중인 정보를 저장하고 불러오는데 시간이 걸림

## 힙/콜스택
- 자바스크립트는 단일 쓰레드이고 콜백 큐를 이용함
- v8엔진의 구성
    - 메모리힙 : 메모리 할당
    - 콜스텍 
        - 함수를 호출할 때 해당함수가 쌓여있는 스택
        - 브라우저는 이 안에 실행할 함수가 있는동안 다른 일 할 수 없음(blocked)
        - 코드가 실행되면서 스택 프레임(함수의 호출 정보) 쌓임
        - 스택 날림 : 콜 스택의 최대 크기에 도달했을 때 발생

### 동시성과 이벤트 루프
- 비동기 콜백
    - 무거운 코드를 문제없이 수행하기 위해

## web api
- web api
    - 개발자가 접근할 수 없는 스래드, 호출만 가능한 명령어
    - dom, AJAX(XMLHttpRequest), Timeout
    - 이에 정이된 함수들은 모두 비동기로 실행된다

## 이벤트 루프의 
- 이벤트 루프
    - 콜스택과 콜백큐를 감시하며, 콜스택이 비어있으면 이벤트 넣음(실행)
        - 이러한 반복을 tick이라고 함
        - 비어있다면 넣는것이기때문에, setTimeout(callback,0)을 해도 콜스택의 코드가 다 실행된 후에 실행된다


### 콜백이란?
- '다시 부른다'
- 다른 코드의 인수로써 넘겨줌. 필요에 따라서 즉시/나중에 실행 가능
- 비동기패턴의 가장 근본적인 부분
- 잘못하면 콜백 지옥에 빠질 수 있음
- 가독성 안좋음
### promise
- 미래의 값, 약속
- 어떤 작업에 성공했을때,promise의 then함수에 넘겨진 파라미터를 단 한 번만 호출하겠다는 약속
- state
    - 대기
    - 이행
        - resolve() 로 실행 
        - then()을 이용해서 처리 결과 값을 받을 수 있음
    - 실패
- new Promise() 로 객체 생성 => resolve/rejsct 매서드 사용 가능
- promise api
    - .then() : 새로운 promise 객체 반환 => then으로 연결해서  promise chaining 가능
    - .resolve() : 주어진 값으로 결정되는 promise.then객체 반환
- 에러처리
    - then()의 두 번째 인자로
    - catch() (가급적 이걸로 하자)

### async/await
- 프로미스 사용을 쉽게 해줌
- await는 async함수 내에서만 사용 가능, 동기적으로 프로미스를 기다릴 수 있게 해줌
    - async 함수의 실행을 일시 중지하고 전달 된 Promise의 해결을 기다린 다음 async 함수의 실행을 다시 시작하고 완료후 값을 반환
- async 함수 선언 : 비동기 함수를 선언함(해당 함수 내에포함되어있는 코드를 수행하는 비동기함수 나타냄)
    - 이 비동기 함수가 호출되면, 프로미스를 반환함  

- async function ...(){     
    ver a = await asdf
}
