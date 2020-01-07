

ansible-inventory
=========

yaml로 작성된 inventory파일 분석 
---------


# Contents  
1. Preknowledge  
2. Structure
3. Image
4. Further
5. References

# Preknowledge
1. 분석파일명
targets1909.yaml
2. 커널
운영 체제의 핵심이 되는 컴퓨터 프로그램의 하나로, 시스템의 모든 것을 완전히 통제한다. 운영 체제의 다른 부분 및 응용 프로그램 수행에 필요한 여러 가지 서비스를 제공한다.

# Structure
1. host
    - build할 서버 정의
    1. magent1
        1. 마스터 노드로 지정 (Further : Master/slave system)
    2. agent2
    3. agent3
2. vars
    - 글로벌 변수 정의
    1. ansible_blahblah : 앤서블로 설치할 때 옵션
    2. cuda : GPU 설치 여부 옵션
    3. ip-port
        - 부가 옵션들의 ip 주소와 포트 설정
        1. db
        2. etcd(further)
        3. redis(further)
    4. manager_config
        - 레지스트리 설정
    5. kernal to install
        - 유저가 설치하고자 하는 커널에 따라 변경
        - 텐서플로우, 파이토치 등
3. children
    - 서버가 여러 개 일 때, 역할별로 객체처럼 나눠 서버 관리
    1. group_db/etcd/redis
        - master, slave 포함 모든 db 설정
    2. group_manager
        - 매니저의 모임
        - CPU용량에 따라서 매니저를 여러 개 생성할수도 있음(further)
        - 파일에는 magent1 하나뿐
    3. group_agent
        - agent의 모임
    4. group_client(further)
        - GUI 없이 커맨드로 명령할 수 있게 하는 기능
        - 여기서 **backend.ai**를 쓸 수 있게 하는걸 클라이언트라함
        `$ backend.ai run python -c "print("a")"`
    5. console-server(파일에 없음)
        - 웹을 이용할 수 있게 하는 서비스
        - 포트 : 8080
    6. wsproxy(파일에 없음)

# Image
![group_manager](structure_of_servers_example.heic)

# Further
- etcd
- redis
- client
- cpu/gpu
- Master/slave system

# References
[모던 스타트업: 팀 생산성을 높여주는 21가지 도구와 서비스]  
https://books.google.co.kr/books?id=59pqDwAAQBAJ&pg=PA143&lpg=PA143&dq=%EC%95%A4%EC%84%9C%EB%B8%94+%EC%9D%B8%EB%B2%A4%ED%86%A0%EB%A6%AC+%ED%8C%8C%EC%9D%BC+yaml&source=bl&ots=pCao1ZJhsm&sig=ACfU3U3nWNGbuR9BkyT6977AtyAXMJrsOg&hl=ko&sa=X&ved=2ahUKEwj9wrqn1fDmAhUUM94KHVAsC-oQ6AEwBXoECAoQAQ#v=onepage&q=%EC%95%A4%EC%84%9C%EB%B8%94%20%EC%9D%B8%EB%B2%A4%ED%86%A0%EB%A6%AC%20%ED%8C%8C%EC%9D%BC%20yaml&f=false

[js yang]
