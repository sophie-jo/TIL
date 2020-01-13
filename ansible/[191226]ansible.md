


Ansible
=========

# Contents
1. Infrastructure as a Code
2. Ansible?
3. 장점
4. 한계
5. 요소

# Infrastructure as a Code
1. 환경의 배포와 구성을 규격화된 코드로 정의해 사용하는 것
2. 환경 자동화 도구
    1. 인프라의 상태를 코드로 선언하고 이를 모든 서버에 배포함으로써 특정 환경을 동일하게 유지할 수 있도록 
    2. 예시 : ansible


# Ansible?
1. 테스트 환경을 구축하는데 사용되는 툴
2. Provision & configuration management tool


# 장점
1. 자동 배포 환경이 쉬움
2. 대부분이 멱등성(Idempotency) 제공
    1. 멱등성
        1. 여러번 적용해도 결과가 바뀌지 않음
        2. 배포되어도 바뀌지 않음
        3. 바뀌는 부분이 있으면 그 부분만 반영
        4. 사용자의 Shell, command, file module 까지는 control 못함
        
# 한계
1. 시스템의 초기 설치 수행은 불가능
    1. 사용자의 OS까지는 설치 못함
    2. Kickstart, pxe등을 사용하면 가능
2. 시스템 모니터링은 지원하지 않음
    1. 사용자가 ansible을 사용하여 설치했을 때 그 시스템이 잘 돌아가고 있는지는 못본다.
    2. Lablup(from js)
        1. 기존에는 다른 툴을 이용해서 했는데, 지금은 버전이 업데이트 되면서 안하고 있다.
        2. js님이 조인하기 전에는 했었음
    3. 내 생각
        1. 하면 좋은거 아닌가
        2.  사용자가 많아질수록 모니터링을 사람이 하긴 어려우므로 나중에 사용자규모가 커졌을 때, 서버 이용자 관리 프로그램을 만들면 어떨까
3. 시스템 변경사항은 추적하지 않음
    1. User : 백엔드.ai의 버전 히스토리 못봄
    2. Provider : 사용자가 backend.ai에서 shell, command, file module을 이용하여 제작한 프로그램에 접근할 수 없음
    3. 내 생각
        1. 백엔드.ai가 프로그래밍을 모르는 사용자들이 편리하게 개발하려고 하는건데, 만약 사용자가 프로그램에 대한 question이나 이용하는데 어려움이 생기면 과연 그 물음을 해결할 수 있는 프로세스 혹은 장치가 있나?


# 요소
1. Inventory
    1. 어디서 수행할지
    2. Infrastructure as a Code의 대상이 될 서버들의 목록을 정의하는 파일
2. Playbook
    1. 무엇을 해야할지
    2. yaml 포맷으로 되어있는 파일
    3. inventory 파일에서 정의된 서버들에서 무엇을 해야할지 정의
3. Module
    1. 어떻게 해야할지
    2. playbook에서 task가 어떻게 수행될지를 나타내는 요소
    3. 500여개 존재
    4. 예시
        1. yum module : yum 명령어를 통해 패키지 설치
        2. debug module : inventory에 정의된 서버에서 디버깅을 위한 각종 값/변수 출력


# References  
[Ansible이란?]  
https://brownbears.tistory.com/358

[Ansible (앤서블) 개념, 사용 환경 구성, 기초 사용법 정리]  
http://blog.naver.com/PostView.nhn?blogId=alice_k106&logNo=221333208746&parentCategoryNo=14&categoryNo=&viewDate=&isShowPopularPosts=true&from=search

created: 2019.12.26  
modified : 2019.12.30
