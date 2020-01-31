

NCP practice (API)
=========

NCP 서버 생성 및 Backend.ai 설치과정 기록    
---------


# Contents  

# Overall process
## 사전준비
1. api header 설정
 - timestamp
 - access key
 - signature
2. signature.py 파일에 requests 라이브러리 추가
3. headers, domain 주소 등 디폴트값 작성
4. api call 코드 작성
5. argparse 라이브러리 추가
 argument로 action?param1=value1&param2=value2... 도메인 뒷부분(서버, 서비스번호 제외) 변수로 받을 수 있도록 설정

## 본격 설치
1. 서버 이미지 리스트 호출
 `python api_call.py -action getServerImageProductList?platformTypeCodeList=LNX64`
 - ubuntu 16.04 
 - serverImageProductCode=SPSW0LINUX000067
2. 서버 프로덕트 리스트 호출
 `python api_call.py -action getServerProductList?serverImageProductCode=SPSW0LINUX000067`
 - standard cpu=2 mem=4
 - serverProductCode=SPSVRSTAND000004

3. 서버 생성
 커맨드라인으로 하면 자꾸 디폴트 옵션으로 생성되서 postman으로 call 했더니 됨
 `GET https://ncloud.apigw.ntruss.com/server/v2/createServerInstances?serverImageProductCode=SPSW0LINUX000067&serverProductCode=SPSVRSTAND000004&serverName=dev1&accessControlGroupConfigurationNoList.1=4198&accessControlGroupConfigurationNoList.2=120849`

