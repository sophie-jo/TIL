
How to increase disk size of VM(virtual machine) created by vagrant
=========

vagrant로 설치한 가상머신의 actual disk size 늘리기
---------


# Contents  
1. Overall process
2. References

# Overall process
0. Reference0 참고
    해결 안됨
1. Refrence1 참고
    gparted GUI가 안열림
2. 원격으로 맥에서 열려고 검색
3. Reference2,3 참고
    1. `sudo apt install x11-xserver-utils` 설치하려함
    2. apt 명령어 안됨
4. Reference4 참고
    1. `brew install x11-xserver-utils`
    2. 패키지 없음


# References
0. [js yang]Vagrant, how to specify the disk size?
https://stackoverflow.com/questions/49822594/vagrant-how-to-specify-the-disk-size

1. Vagrant Box 디스크 용량 늘리기
https://chrislee.kr/wp/2016/10/15/vagrant-box-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9A%A9%EB%9F%89-%EB%8A%98%EB%A6%AC%EA%B8%B0/

2. xhost 명령과 display옵션 사용하기 – xhost,oracle,display옵션
http://blog.topmania.com/?p=1026

3. ssh와 xhost를 통해 원격으로 GUI를 사용해 보자.
https://m.blog.naver.com/PostView.nhn?blogId=occidere&logNo=221133121595&proxyReferer=https%3A%2F%2Fwww.google.com%2F

4. How to install apt-get or YUM on Mac OS X
https://unix.stackexchange.com/questions/80711/how-to-install-apt-get-or-yum-on-mac-os-x

