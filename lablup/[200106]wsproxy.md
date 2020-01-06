

wsproxy
=========

magent1 서버에 wsproxy 설치해서 세션 실행가능하게 함
---------


# Contents  
1. Reason
2. Installation process 
3. Further
4. References


# Reason
HTTP를 전송하기 위해 TCP가 필요한데 TCP를 사용하기 위해서는 ws proxy가 필요함(Further)
Client와 Backend.ai 서버를 연결해서 앱을 사용할 수 있게 하기 위해 필요 (앱 : 주피터 노트북 등)
1. 회사에 backend.ai를 설치
2. Client가 300명 정도 되는데 각 client가 앱을 3개 씩 쓴다면 : 900개의 포트가 필요
3. 900개를 열 수는 없기에 ws proxy 이용
4. 클라이언트와 서버의 중간다리 역할
    트래픽 변환해줌
5. User 입장
    - 터미널로 서버 접속하는 유저들은 ws proxy 불필요
    - 웹으로 서버 이용하는 유저들을 위해 필요    


# Installation process 
1. Download wsproxy docker image on magent1 server 
(https://s3.ap-northeast-2.amazonaws.com/backend.ai/offline-installers/ansible/appproxy_201911.tar.gz)

2. Download wsproxy.simple.yaml on magent1 server and replace the IP address(10.231.238.171 ) with the IP address of your magent1 (10.100.64.50)
```scp wsproxy.simple.yaml vagrant@10.100.64.50:~/```

3. Loading docker image on magent1 server
```gunzip -c appproxy_201911.tar.gz | docker load``` 

4. Start wsproxy docker
```docker-compose -f wsproxy.simple.yaml -p pycon2019 up -d```

5. Now you can test Backend.AI Web GUI. 


# Further
[TCP/IP/HTTP]
https://asfirstalways.tistory.com/85
https://brunch.co.kr/@wangho/6



# References
[kj cho]