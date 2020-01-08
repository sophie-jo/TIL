

CPU & GPU
=========

공통점과 차이점
---------


# Contents  
1. 공통점
    - 둘 다 데이터를 읽어들여 연산처리를 통해 답을 도출하는 기능을 수행
    - 컴퓨터에서 두뇌 역할을 하는 점에서 비슷
2. CPU(Central Processing Unit)
    - 입력 받은 명령을 해석 / 연산 한 후, 이를 통해 결과 값을 출력 장치로 전달하는 컴퓨터의 주요 부품
    - 성능지표
        1.클럭(동작속도)의 수치
            높을수록 단일 작업을 빠르게 처리하는 데 유리
        2.코어(핵심 회로)의 수
            많을수록 멀티태스킹/멀티코어 연산에 최적화된 프로그램을 구동하는데 유리
        3.캐시 메모리(임시 저장소)의 용량
            클수록 덩치가 큰 프로그램을 구동하거나 자주 하는 작업을 반복 처리할 때 작업 효율을 높일 수 있음
3. GPU(Graphics Processing Unit)
    - 최초목적 
        병렬연산에 특화된 구조를 통한 높은 3d 그래픽 처리
    - 최근
        - GPGPU(General Purpose computing on Graphics Processing Units) 기술으로 이외의 범용 작업에도 GPU의 처리 능력을 보탬
4. 차이점
    - CPU : 명령어가 입력된 순서대로 데이터를 처리하는 직렬 처리방식에 특화
    - GPU : 여러 명령을 동시에 처리하는 병렬 처리 방식에 특화

# Further
cuda

# References
[CPU와 GPU의 차이]
https://light-tree.tistory.com/25


