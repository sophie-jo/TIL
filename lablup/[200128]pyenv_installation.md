

pyenv 설치(Ubuntu)
=========

backend.ai 설치 위해 python 3.5.2이상의 환경 만들기
---------


# Contents  
1. Process 
2. Cause
3. References

# Process
1. 설치
 `curl https://pyenv.run | sh`
2. bash파일에 추가
 `vi .bashrc` 파일의 끝에 다음 추가
    `export PATH="/home/ubuntu/.pyenv/bin:$PATH"`
    `eval "$(pyenv init -)"`
    `eval "$(pyenv virtualenv-init -)"`
3. 수정된 bach파일 읽기
 `source .bashrc`


# Cause
파이썬 환경이 충돌하기가 쉽기 때문에 pyenv로 가상환경 만들고 backend.ai설치할는게 쉬움

# References
js yang