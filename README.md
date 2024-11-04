메모를 CRUD할 수 있는 WEB Application을 만드는 실습을 했다.
Create: 메모 생성하는 기능
Read: 메모한 걸 조회하는 기능
Update: 메모 전체를 수정하는 기능
Delete: 메모한 걸 삭제하는 기능


각 메모는 식별자(id), 제목(title), 내용(contents)으로 구성된다.

- HTTP API 설계
    - 로그인과 같은 특별한 기능을 제외한 대부분의 API는 CRUD 작업을 수행한다.
    - 설계 순서
        1. HTTP Method
            - POST : CREATE
            - GET : READ
            - PUT, PATCH : UPDATE
            - DELETE : DELETE
        2. Restful API → URL Mapping
        3. 요청 및 응답값 설계
        - HTTP Method + URL 만으로 어떤 API인지 구분할 수 있어야 한다.
    - 메모 생성
        - POST
        - /memos
    - 메모 단건 조회
        - GET
        - /memos/{id}
    - 메모 수정(전체)
        - PUT
        - /memos/{id}
    - 메모 삭제
        - DELETE
        - /memos/{id}

- 문제점
  - 실제 문제의 원인을 파악하기 어렵거나 잘못된 정보 전달 및 처리가 될 수 있다.
            1. 응답 코드가 세분화 되지 않았다
            2. 적절한 예외가 발생하지 않는다(실패 시 모두 500 Error 발생))
  -서버가 종료된 후 다시 켜지면 데이터가 모두 초기화 된다.
