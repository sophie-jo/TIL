

AWS practice (CLI)
=========

AWS EC2 가상머신에 backend.ai client 설치하고 세션 생성 및 텐서플로우 코드 실행     
---------


# Contents  
1. Overall Process
2. Details
3. Problem and solution
4. References

# Overall Process
1. brew로 awscli 설치
    `brew install awscli`
2. configure 
    `Sophies-Mini:aws sophie$ aws configure`
    `AWS Access Key ID : AKIAQX672R265GXYJBAX`
    `AWS Secret Access Key : 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`
    `Default region name [None]: ap-northeast-2`
    `Default output format [None]:`
3. 인스턴스 생성
    `aws ec2 run-instances --image-id ami-025376d8670c1a73f --instance-type t2.micro`
4. 인스턴스 시작
    `aws ec2 start-instances --instance-ids i-03bf26e510547a159`
5. key pair 생성
    `aws ec2 create-key-pair --key-name sophie1 --query 'KeyMaterial' --output text > sophie1.pem`
6. 서버 접속
    `bai-cloud ssh-instance dev1`

# Detatils
1. 3 인스턴스 생성 커맨드라인 옵션
 * image-id : Ubuntu 16.04
    `aws ec2 describe-images`에서 찾음
 * instance-type 
    t2.micro (프리티어)
 
    
# Problem and solution
1. 인스턴스 시작 후 서버에 접속하고 싶은데 ssh로는 안됨
 키페어 생성

 
# References
1. jg kim
2. aws_ssm_agent
