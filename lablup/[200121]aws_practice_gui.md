

AWS practice (GUI)
=========

AWS EC2 가상머신에 backend.ai client 설치하고 세션 생성 및 텐서플로우 코드 실행     
---------


# Contents  
1. Overall Process
2. Details
3. Problem and solution
4. References

# Overall Process
1. AWS 가입
2. EC2 사용 가상머신 시작
3. Amazon Machine Image(AMI) 선택(Ubuntu 16.04)
4. 인스턴트 유형 선택/실행
5. 인스턴트에 연결 - 독립 실행형 SSH 클라이언트
6. 터미널 - 프라이빗 키 있는 디렉토리로 이동
7. 서버 접속
    `chmod 400 sophie.pem`
    `ssh -i "sophie.pem" ubuntu@ec2-3-19-244-129.us-east-2.compute.amazonaws.com`
7. backend.ai client 설치
    `sudo pip3 install backend.ai-client`
8. backend.ai 실행
9. 엔드포인트 및 타입 설정
    `export BACKEND_ENDPOINT=https://cloud.backend.ai`
    `export BACKEND_ENDPOINT_TYPE=session`
10. 로그인
    `backend.ai login`
11. 텐서플로우 예시 코드 생성(mnist.py)
12. 코드 실행(커맨드라인)
    1. 세션 자동으로 생성 후 실행
     `backend.ai run --rm --exec 'python mnist.py' -r cpu=4 -r mem=8g -r cuda.shares=2 -g beta-user python-tensorflow:2.0-py36-cuda9 ./mnist.py`
     `backend.ai run --rm -c 'print("hello world")' -g beta-user python:3.6-ubuntu18.04`
    2. 세션 수동으로 생성 후 실행
     `backend.ai start -r cpu=4 -r mem=8g -r cuda.shares=2 -g beta-user python-tensorflow:2.0-py36-cuda9`
     `backend.ai run --session-id 93d8b6df66 --exec 'python mnist.py' python-tensorflow:2.0-py36-cuda9 ./mnist.py`
    3. 세션 확인
     `backend.ai ps`
13. 코드 실행(jupyter)
    1. local proxy 실행
     `backend.ai app ac62ea1294 jupyter -b 0.0.0.0:8080`
    2. 웹브라우저로 다음 주소에 접속
     3.19.244.129:8080
    3. 새로운 ipynb 파일 생성
     new - tensorflow2.0 python3.6 cuda9.0
    4. 예제코드 입력
    5. Run cell


# Detatils
1. 12-1 코드
    * options
     --rm : 실행후 자동으로 세션 삭제
     --exec 'shell command' : 파이썬 파일 실행위한 쉘커맨드 입력
     -c 'code snippet' : 파일없이 코드만 실행할 때
     -r : 리소스 할당 (cpu, memory, gpu)
     -g : Group name where the session is spawned, 연구/과제 그룹이 있으면 그걸로
    * image 
     python-tensorflow:2.0-py36-cuda9
2. 12-2 코드
    실행할 때 생성한 세션id 입력해야함
3. 13-3 주소
    AWS 인스턴스의 public IP : 3.19.244.129
    port : 8080

# Problem and solution
1. group 옵션
    `✘ [0] BackendAPIError(400, 'Bad Request', {'type': 'https://api.backend.ai/probs/invalid-api-params', 'title': 'Missing or invalid API parameters. (Invalid group)'})`
    `-g beta-user` 옵션 추가
    보통은 디폴트값이 있어서 안줘도 되는데 베타라서 줘야 함
2. 웹 접속 안됨
    `ubuntu@ip-172-31-25-152:~$ backend.ai app ac62ea1294 jupyter`
    `∙ A local proxy to the application "jupyter" provided by the session "ac62ea1294" is available at: http://127.0.0.1:8080`
    1. 
    커맨드에 bind 옵션 추가(13-1 코드 참고)
        `-b 0.0.0.0:8080`
    AWS 인스턴스 보안그룹 중 launch-wizard1
    인바운드 탭-편집-규칙추가-저장
        - 유형 : 사용자 지정 TC
        - 프로토콜 : TCP
        - 포트 : 8080
        - 소스 : 내 IP
    2. vpn 이용하여 로컬 주소로 접속


 
# References
1. [5.EC2 리눅스 인스턴스 접속 방법](https://goddaehee.tistory.com/181)
2. [Backend.AI Client SDK for Python](https://docs.client-py.backend.ai/en/19.09/cli/sessions.html)
3. jk shin
4. jg kim
