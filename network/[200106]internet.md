

Internet/server/network
=========


# Contents

* 구조
1. Client (PC)
2. Server (google.com)

* 상호작용
1. Client->Server : request
2. Server->Client : response

* Web browser
    * PC가 서버에 접속할 수 있게 하는 도구
    * 종류
     1. firefox
     2. internet explorer
     3. chrome
    * 서버에 접속하는 법
    1. IP address (171.21.25.78)
    2. Domain name (google.com)
        client가 입력하면 DNS서버에 접속되어 입력한 도메인의 IP 주소를 반환

* DNS server
    - 이 세상 모든 도메인이 각각 어떤 ip를 가지고 있는지 저장하고 있는 서버
    - 거대한 전화번호부

* IP address
    * 종류
    1. Public address
        - ifconfig로 확인
        - 외부 서버와 접속시 사용하는 주소
    2. Private address
        - ipinfo.io 접속해서 확인
        - 각각의 computer 식별 가능
    * 차이
    1. Public/Private 같을 때
    통신사의 네트워크와 바로 연결되어 있을 때  
    모든 computer를 일일히 연결하려면 비용이 많이 듦  
    2. 다를 때
    통신사의 네트워크와 Router가 연결되어 있을때  
        1. 통신사-router : public address
        2. router-computers : private addresses




# References  
[인터넷, 네트워크 그리고 서버]  
https://opentutorials.org/course/2598/14427
[웹서버(아파치)]  
https://opentutorials.org/course/2598/14446
