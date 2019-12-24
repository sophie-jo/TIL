Local computer가 Server computer에 접근하는 법 (mac)
================================================

SSH의 자동 로그인 기능을 통해서 편리하게 git 사용하기
------------------------------------------------



# Contents
1. Preknowledge
2. Overall process
3. Details
4. Reference



# Preknowledge
* Local computer  
내 맥북
* Server computer  
깃허브  
원격 저장소
* 깃허브?통신방식  
	- ssh : 매번 로그인 안해도 됨
	- https

# Overall process
1. Open terminal
2. ssh-keygen 입력
	1. Output : 경로 
3. enter 3번 
4. 2.1로 이동
5. 두 개의 파일 생성됨
	1. id_rsa
	2. id_rsa.pub
6. cat id_rsa.pub
	1. Output : 텍스트
	2. Do : Copy
7. Github 접속
8. 프로필 사진을 클릭하면 나오는 settings 
9. SSH and  GPG keys 
	1. New SSH key
		1. Title
		Local computer 이름 설정
		2. Key
		6.1를 Paste
	2. Add SSH key
10. 확인
	1. 새 repo 생성
	2. 주소(ssh) Copy
	3. Open terminal
	4. Git clone + 10.2 paste + Local computer에 생성될 폴더명
	5. yes
	6. 10.4의 폴더로 이동
	7. vim 에디터로 아무 파일 생성
	8. git add 10.7.txt
	9. git commit -m blahblah
	10. git push
	잘 되면 성공한거
	



# Details  
5.두 개의 파일 생성됨  
	5.1 id_rsa  
		private key(비밀번호)  
		Local computer에 저장  
	5.2 id_rsa.pub  
		public key(공개된 정보)  
		Server computer에 저장  
	부연설명  
		5.2를 Copy해서 Server computer에 접속  
		5.1를 만들 때 5.2가 같이 생성  
		Server computer에 접속할 때 비밀번호 입력하지 않고 자동으로 두 개의 Computer 사이에 여러 복잡한 절차가 일어남  
		결국 안전하게 Local computer가 Server computer에 자동로그인  
	image  
<img src=“/img/local_and_server_computers.png” title=“Relationship btw id_rsa and id_rsa.pb”></img>  
6. cat id_rsa.pub  
	cat : 파일 내용 화면에 출력  
9. SSH and  GPG keys  
	여기서 github에 내 공개키를 저장  



# References  
https://www.youtube.com/watch?v=78rykXw9_0g

