

NCP practice (GUI)
=========

NCP 서버 생성 및 Backend.ai 설치과정 기록    
---------


# Contents  
1. Overall Process
2. Details
3. Problem and solution
4. References

# Overall Process
## 서버 생성 
1. NCP login
2. Console 접속-서버 생성
3. 서버 이미지 선택
 - 부팅 디스크 크기 : 50GB
 - 이미지타입 : OS
 - OS 이미지 타입 : CentOS
 - 서버 타입 : Micro (1년간 무료)
 - 서버 이미지 이름 : Centos-7.3-64
4. 서버 설정
 - Zone : KR-2
 - 스토리지 : HDD
 - 서버타입 : Micro (vCPU=1, mem=1GB, disk=50GB)
 - 요금제 : 월요금제
 - 서버 개수 : 1
 - 서버 이름 : dev 
 - 반납 보호 : 해제
5. 인증키 설정
 - 보유하고 있는 인증키 이용 : nbp
6. 네트워크 접근 설정
 - 보유하고 있는 ACG 중에서 선택(Access Control Group)
    - ncloud-default-agc
    - manager-agc
7. 최종 확인 후 서버 생성
    서버에 로그인하기 위해서는 먼저 포트포워딩을 설정해야 합니다.
    그 후, 설정한 포트포워딩 IP와 포트에 대해 ACG 설정을 완료하시면 서버 접속이 가능합니다.
    외부에 서비스를 하기 위해서는 먼저 공인 IP 생성이 필요합니다.
    생성한 공인 IP를 서비스하고자 하는 서버에 할당한 후, 공인 IP에 대한 ACG 설정을 완료하시면 서비스가 가능합니다.
8. 포트 포워딩
    - 서버 접속용 공인 IP(자동생성)
    - 외부 포트 : 8080 (수동생성)
9. 관리자 비밀번호 확인
    - 인증키 불러오기
    - 비밀번호 확인

## 서버 접속
1. 터미널에서 ssh로 root 계정에 접속
 `ssh root@45.119.145.186 -p 8080`
2. 비밀번호 : 관리자 비밀번호 붙여넣기
3. 계정 생성
 `adduser sophie`
4. 비밀번호 생성
 `passwd sophie`

## Backend.ai 설치
1. 암호없이 로그인 할 수 있도록 설정
 `ssh-copy-id sophie@45.119.145.186 -p 8080`
2. ansible inventory 파일 수정 후 설치

 
# References
1. js yang
