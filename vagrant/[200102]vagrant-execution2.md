vagrant-execution2
=========

vagrant가 이용하는 이미지 박스 버전 바꾸기
---------

# Contents  
1. Problem
2. Solution
3. Reference


# Preknowledge  
1. [191227]vagrant-basic.md
2. Box 
vagrantfile 안에 있는 ubuntu/bionic64

# Problem
vagrant up 하면 세 개의 서버가 한꺼번에 설치되지 않고 하나씩 설치됨

# Assumed cause
박스 버전이 달라서 그런 것


# Solution
1. 기존 박스를 지움
```vagrant box remove ubuntu/bionic64 --box-version=20191218.0.0```
2. js님이 말한 버전 추가
```vagrant box add ubuntu/bionic64 --box-version 20190905.0.0```

# Result
해결 안됨

# Reference  
1. delete vagrant box . 
https://laracasts.com/discuss/channels/general-discussion/delete-vagrant-box?page=1
2. command line for vagrant box . 
https://www.vagrantup.com/docs/cli/box.html
