

Ansible
=========

# Contents
1. Ansible이란?
2. 장점
3. 한계


# Ansible이란?
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

# References  
[Ansible이란?]
https://brownbears.tistory.com/358