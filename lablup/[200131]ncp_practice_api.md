

NCP practice (API)
=========

NCP 서버 생성 및 Backend.ai 설치과정 기록    
---------


# Contents  

# Overall process
## 사전준비
1. api header 설정
 - timestamp
 - access key
 - signature
2. signature.py 파일에 requests 라이브러리 추가
3. headers, domain 주소 등 디폴트값 작성
4. api call 코드 작성
5. argparse 라이브러리 추가
 argument로 action?param1=value1&param2=value2... 도메인 뒷부분(서버, 서비스번호 제외) 변수로 받을 수 있도록 설정

## 서버 생성
1. 서버 이미지 리스트 호출
 `python api_call.py -action getServerImageProductList?platformTypeCodeList=LNX64`
 - ubuntu 16.04 
 - serverImageProductCode=SPSW0LINUX000067

2. 서버 프로덕트 리스트 호출
 `python api_call.py -action getServerProductList?serverImageProductCode=SPSW0LINUX000067`
 - standard cpu=2 mem=4
 - serverProductCode=SPSVRSTAND000004

3. 서버 생성
 커맨드라인으로 하면 자꾸 디폴트 옵션으로 생성되서 postman으로 call 했더니 됨
 `GET https://ncloud.apigw.ntruss.com/server/v2/createServerInstances?serverImageProductCode=SPSW0LINUX000067&serverProductCode=SPSVRSTAND000004&serverName=dev1&accessControlGroupConfigurationNoList.1=4198&accessControlGroupConfigurationNoList.2=120849`
 - serverImageProductCode=SPSW0LINUX000067
 - serverProductCode=SPSVRSTAND000004
 - serverName=dev1
 - accessControlGroupConfigurationNoList.1=4198
 - accessControlGroupConfigurationNoList.2=120849

4. 포트 포워딩
    1. 포트포워딩 룰 리스트 조회 - config no. 얻기 위해
     `python api_call.py -action getPortForwardingRuleList`
    2. 서버 인스턴스 조회 - server instance no. 
     python api_call.py -action getServerInstanceList
    3. 포트 포워딩 설정
     `python api_call.py -a addPortForwardingRules -p portForwardingConfigurationNo=64169 -p portForwardingRuleList.1.serverInstanceNo=3569262 -p portForwardingRuleList.1.portForwardingExternalPort=8080 -p portForwardingRuleList.1.portForwardingInternalPort=22`
     - portForwardingConfigurationNo=64169
     - portForwardingRuleList.1.serverInstanceNo=3569262
     - portForwardingRuleList.1.portForwardingExternalPort=8080
     - portForwardingRuleList.1.portForwardingInternalPort=22

5. 관리자 비밀번호 확인(인증실패)
 `python api_call.py -a getRootPassword -p serverInstanceNo=3569262 -kf nbp.pem`
  Problem : Private key 인증 실패




## NAS 생성
1. NAS 생성
 `python api_call.py -a createNasVolumeInstance -p volumeName=testnas -p volumeSize=100 -p volumeAllotmentProtocolTypeCode=NFS -p serverInstanceNoList.1=3569262 -p serverInstanceNoList.2=3587800`

## 서버 접속 및 설치 사전준비
1. 터미널에서 ssh로 root 계정에 접속
 `ssh root@106.10.54.23 -p 8080`
2. 비밀번호 : 관리자 비밀번호 붙여넣기
3. 계정 생성
 `adduser dev`
4. 비밀번호 생성
 `passwd dev`
5. 암호없이 로그인 할 수 있도록 설정
 `ssh-copy-id dev@106.10.54.23 -p 8080`
6. dev 계정 접속
 `ssh dev@106.10.54.23 -p 8080`
7. sudo로 root 접근 권한 허용
 `sudo su`
 `sudo 비밀번호 설정`
8. agent1 서버에 대해서도 1~7 반복
 sudo 패스워드 동일하게 설정

## Backend.ai 설치
1. ansible inventory 파일 수정 후 설치
ansible-playbook -i targets1915.yaml   scripts/install_backend_ai_rolebased2.yaml -K -e "operation=install"

2. 문제
    1. "\r\ndev is not in the sudoers file.
    /etc/sudoers 에 dev1 추가
    https://blog.outsider.ne.kr/505

    2. unable to resolve host dev1
    /etc/hosts에 /etc/hostname에 있는거 추가
    https://gentooboy.tistory.com/238

