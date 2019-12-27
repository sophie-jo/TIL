

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


# References  
https://right-hot.tistory.com/entry/%EA%B9%83%ED%97%88%EB%B8%8C-pull-%EC%B6%A9%EB%8F%8C-%EC%97%90%EB%9F%AC-Please-commit-your-changes-or-stash-them-before-you-merge