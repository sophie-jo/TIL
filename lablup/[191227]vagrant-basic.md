

vagrant-basic
=========



# Contents  
1. Preknowledge
2. Vagrant?


# Preknowledge 
* Provisioning
사용자의 요구에 맞게 시스템 자원을 할당, 배치, 배포해 두었다가 필요 시 시스템을 즉시 사용할 수 있는 상태로 미리 준비해 두는 것

# Vagrant?  
* Vagrant란? 
    * 운영체제 시스템에 쉬운 provisioning을 할 수 있게 하는 도구
    * 주로 가상머신을 생성하고 관리할 때 사용
    * 가상머신(VM) 설정
        *  사용자의 요구에 맞게 Host name, IP, Service Install 
    * 가상머신 이용
        * 사용자가 원할 시 해당 시스템을 즉시 사용할 수 있도록
* 가상머신 생성 및 관리
    1. vagrant 없을 때
        * Virtual box에서 각각 개별 가상머신을 생성하고 접속하여 한대씩 설정해야 함
            1. Hostname
            2. IP
            3. Service
            4. etc
    2. vagrant 사용할 때
        * vagrantfile을 통하여 해당 파일에 가상머신에 대한 설정과 해야할 작업 미리 정의
        * virtual box를 통하여 provisioning
        * 가상머신 간편하게 생성, 관리 가능


# References
1. preknowledge
https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EB%B9%84%EC%A0%80%EB%8B%9D
2. Vagrant  
[Vagrant 설치 및 기초 사용방법]
https://ossian.tistory.com/86
3. Vagrant command line
https://www.vagrantup.com/docs/cli/box.html

