

Ansible test2
=========

Ansible test1을 자동화하기
---------


# Contents  
1. Overall process 
2. Problem and Solution
3. References


# Overall process
1. VM 활성화 (vagrant)
2. ansible directory 이동
3. 테스트 실행
    `ansible-playbook -i targets1910.yaml scripts/test_tensorflow_session.yaml -e  "operation=test"`
ansible-playbook -i targets1910.yaml scripts/test_tensorflow_session3.0.yaml -e  "operation=test"
4. 모듈화 진행
run_test_tensorflow.yaml 라는 task 파일 생성
test 하는 파일에서 include tasks로 불러올 수 있게
전달 변수 : test_code.py 
5. 일반화 진행
* root file : scripts/ansible_test.yaml
* include task
 1. test/set_test_environment.yaml 
 2. test/run_test_tensorflow.yaml
* parameters(variables)
 1. test_code_file: 'test_code_tensorflow.py'
 2. kernal_image: 'lablup/python-tensorflow:1.14-py36'


# Problem and Solution
1. 
 * Problem : operation 설정이 안됨
 * Solution
    roles/reading_defaults/defaults/main/reading_operation.yaml
    위 파일에 "test" in operation 추가
    Command line 
    `ansible-playbook -i targets1910.yaml scripts/test_tensorflow_session.yaml -e  "operation=test"`
2. 
 * Problem : scripts 파일 안의 쉘 커맨드 라인에서 backend.ai 가 안됨
    `'backend.ai run -t test_session_1 -r cpu=2 -r mem=4g lablup/python-tensorflow:1.14-py36 main.py'`
 * Solution
    1. backend.ai 부분을 다음과 같이 수정
     `source .bashrc && {{ venv_client_backend_ai_path.stdout }}`
    2. task 추가
     store pyenv execution string
     get client python symbolic link
     debug
3. 
 * Problem
   `"BackendAPIError: 401 Unauthorized", "Credential/signature mismatch."`
 * cause
    public key를 읽어오지 못해서
 * solution
    run test task의 environment 부분 수정
4. 
 * Problem
    `No such file or directory: '/home/vagrant/test_code.py`
 * cause
    test code 복사를 client 디렉토리 안으로 했기 때문
 * solution
    scripts 파일 안의 쉘 커맨드 라인 수정
    `'backend.ai run -t test_session_1 -r cpu=2 -r mem=4g lablup/python-tensorflow:1.14-py36 client/main.py'`
    
# References
js yang




