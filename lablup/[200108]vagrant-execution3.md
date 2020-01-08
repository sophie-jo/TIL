vagrant-execution
=========

vagrantfile로 직접 가상머신 생성하기
---------

# Contents  
1. Preknowledge
2. overall process
3. Details



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
