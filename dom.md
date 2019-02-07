# DOM

### 알아둬야 할 것
- dom이란?
- 이벤트 버블링,캡쳐링,위임
- 메뉴에 따라 내용이 달라지는 문서 만들어보기
- dom조작- 순회,추가,삭제,이동
- event handling(EventListener,Event object)
- event handling(keyboard control- form control)
- 동적 엘리먼트 스타일 다루기

## 이벤트 버블링 
- 이벤트가 상위 요소들로 전달됨
    - 하위 -> 상위 

## 이벤트 캡쳐
- 이벤트가 상위 요소에서 하위 요소로 탐색됨
    - 상위 -> 하위
- addEventListener()에서 옵션 객체에 capture:true를 설정해주면 됨

### event.stopPropagation()
- 이벤트가 전파되는것을 막음
- 해당 이벤트 함수에 event.stopPropagation()을 써서 사용

## 이벤트 위임
- 하위 요소에 각 이벤트를 붙이지 않고 상위 요소에 리스너를 붙이고 하위에서 발생한 이벤트 감지
- ex)

## dom조작
- ### 순회

- ### 추가
    - innerHTML/innerTEXT 프로퍼티 사용
    - 이 프로퍼티를 사용하지 않을 때
    - 순서 
        1. 요소 노드 생성 / creatElement(tagname)메소드 이용
        2. 텍스트 노드 생성/ creatTextNode(Text) 메소드 이용 / 
        3. DOM에 추가 /appendChild(Node) 메소드 이용
        
- ### 삭제
    - removeChild 메소드 이용하여 삭제

- ### 이동
## event handling
이벤트를 처리하는 것    
- EventListener
    - TargetEvent객체로부터 발생한 이벤트를 처리하기 위한 오브젝트
    - element.addEventListener('이벤트',실행될 함수)
        - ex)<pre><code>
                const a = document.getElementById('a');
                a.addEventListener('click',event);
                function event(){}
            <code><pre>
    
- EventObject(이벤트객체)
    - dom에서 관련 이벤트가 발생하면 정보는 모두 여기에 담김
    
- keyboard control
- form control

## 동적 엘리멘트 스타일 다루기
- 동적으로 css를 변경
    - 엘리먼트.style.변경할 속성(프로퍼티)
        - ex)element.style.color = '#fff';