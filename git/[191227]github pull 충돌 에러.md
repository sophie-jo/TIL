

github pull 충돌 에러
=========

한 로컬저장소에서 github에 push했는데 다른 로컬저장소에서 pull 이 안될 때
---------


# Contents  
1. Problem  
2. Solution
3. References


# Problem  
회사 맥에 어제 집에서 수정한거 pull 하려는데 다음과 같이 뜸  
```error: Your local changes to the following files would be overwritten by merge:
 	.DS_Store
Please commit your changes or stash them before you merge.
Aborting
```

# Solution  
```
Sophies-Mini:TIL sophie$ git pull git@github.com:sophie-jo/TIL.git
Are you sure you want to continue connecting (yes/no)? yes
Sophies-Mini:TIL sophie$ git add .
Sophies-Mini:TIL sophie$ git commit -m "commit error"
Sophies-Mini:TIL sophie$ git push origin master
Sophies-Mini:TIL sophie$ git pull origin master
```

* .DS_store 삭제
`sudo find / -type f -name '\.DS_Store' -print -delete`

* .DS_store 생기지 않게
`defaults write com.apple.desktopservices DSDontWriteNetworkStores ture`

# References  
1. 
https://right-hot.tistory.com/entry/%EA%B9%83%ED%97%88%EB%B8%8C-pull-%EC%B6%A9%EB%8F%8C-%EC%97%90%EB%9F%AC-Please-commit-your-changes-or-stash-them-before-you-merge

2. 맥에서 '.DS_store'가 생기는 이유와 지우는 방법
https://nine-hundred.github.io/Blog/DS_store%EA%B0%80-%EC%83%9D%EA%B8%B0%EB%8A%94-%EC%9D%B4%EC%9C%A0%EC%99%80-%EC%82%AD%EC%A0%9C%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95/


20.1.10 추가

