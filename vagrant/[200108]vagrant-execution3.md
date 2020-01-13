vagrant-execution3
=========

vagrantfile로 직접 가상머신 생성하기
---------

# Contents  
1. Preknowledge
2. Overall process
3. Details
4. Problem
5. Cause
6. Solution
7. Reference


# Preknowledge  
* 파일
Vagrantfile

# overall process
1. 기존 서버 3개 삭제 (magent1, agent2, agent3)
`vagrant destory`
2. 옛날에 서버 3개 설치한 Vagrantfile에서 magent1만 남도록 수정
3. 가상 서버 생성
`vagrant up`


# Details  
* host name은 어떤 걸로 해도 상관없음
    원래 manager로 되어있는 걸 magent1로 수정

# Problem
가상머신 생성 후 서버 접속하려는데 다음과 같은 오류가 뜸
`Mac-mini:backend.ai-ansible-master sophie$ ssh vagrant@10.100.64.50`
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:vmGVDekQHjfuOE0A7Tt7XYzq9rhkwdI8lcUby+lEkBI.
Please contact your system administrator.
Add correct host key in /Users/sophie/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /Users/sophie/.ssh/known_hosts:2
ECDSA host key for 10.100.64.50 has changed and you have requested strict checking.
Host key verification failed.
```

# Cause
10.100.64.50라는 IP로 기존에 접속한 적이 있는 서버와 RSA 공유키를 교환한 상태에서 10.100.64.50서버가 바뀌었기 때문

# Solution
key 초기화
`ssh-keygen -R 10.100.64.50`

# Reference
[SSH 접속시 RSA 공유키 충돌 문제 해결]  
https://cpuu.postype.com/post/30065