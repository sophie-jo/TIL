ansible-scripts
=========

yaml로 작성된 ansible 설치 playbook 파일 분석
---------


# Contents  
1. Preknowledge  
2. Structure
3. Image
4. Further
5. References

# Preknowledge
* 분석파일명
install_backend.ai_rolebased2.yaml

# Structure
* 여러 개의 role들로 구성
1. name : 역할 이름
2. hosts : 대상 설정 (ex : group_db)
3. gather_facts 
    - 대상에 대해 ssh로 접속한 다음에 접속이 잘 되는지 확인
    - 대상에 대한 정보 참조
4. tasks : 순차적으로 수행할 목록
    1. include_role 
    role 디렉토리에 있는 것들 찾아서 수행
    2. include_task
    task 디렉토리에 있는 파일 찾아서 수행
    3. vars : role이나 task에 대한 옵션들
    - target_directory_to deploy : 설치할 디렉토리가 없으면 만들어라
    - {{~~~}} 
        - 유저마다 달라지는 것
        - gather_facts이용해서 inventory에서 정보 참조



# References  
[js yang]