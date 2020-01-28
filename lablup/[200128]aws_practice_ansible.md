

aws practice ansible
=========

aws instance에 ansible로 backend.ai 설치하기
---------


# Contents  
1. 인벤토리 파일 수정 
 target1913.yaml
 * 수정 내용
 - ansible_host : ec2-54-180-144-96.ap-northeast-2.compute.amazonaws.com
 - host_ip: private ip
 - ansible_user: ubuntu
 - ansible_ssh_private_key_file: ~/aws/backend.ai-cloud-scripts/sophie2.pem

2. 앤서블 커맨드라인 입력
`backend.ai-ansible-master sophie$ ansible-playbook -i targets1913.yaml   scripts/install_backend_ai_rolebased2.yaml -K -e "operation=install"`



# References
js yang
