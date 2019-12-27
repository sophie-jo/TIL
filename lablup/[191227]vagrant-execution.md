vagrant-execution
=========

vagrantfile로 직접 가상머신 생성하기
---------

# Contents  
1. Preknowledge
2. overall process
3. Details
4. Problem
5. Solution
6. Reference


# Preknowledge  
[191227]vagrant-basic.md

# overall process
1. js님께 파일받음 (vagrantfile_original)
2. 수정 (vagrantfile_revised)
3. 3개의 가상머신 생성

# Details  
* original file에서 수정한 점
    1. script 안의 키를 나의 퍼블릭키로 변경
    2. magent1, agent2, agent3의 ip address 변경
    3. bridge(네트워크 인터페이스) 변경

# Problem
* 처음에 bridge를 바꾸지 않고 시작함
    * magetnt1 설치할 때 목록이 주어짐
        *  1) en1: Wi-Fi (Wireless)
        *  2) en0: Ethernet
        *  3) en6: USB Ethernet(?)
        *  4) en2: Thunderbolt 1
        *  5) en3: Thunderbolt 2
        *  6) en4: Thunderbolt 3
        *  7) en5: Thunderbolt 4
        *  8) bridge0
        *  9) p2p0
        *  10) awdl0
    * 하나 선택 (1)

# Solution
* agent2,3 부터는 자동으로 bridge가 선택되게 하기 위해서
    * vagrantfile의 bridge 부분에 Wi-Fi(Wireless) 넣음

# Reference  
[vagrant와 virtualbox를 이용한 개발환경]
https://comafire.github.io/pages/platform-vagrant-virtualbox/