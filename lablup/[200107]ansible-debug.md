

ansible-debug
=========

yaml로 작성된 debug모듈 플레이북 실행
---------


# Contents  
1. Preknowledge  
2. Structure
3. Command
4. Result
5. Reference

# Preknowledge
* 파일명
debug_print_fact_vtype.yaml


# Structure
파일내 task가 debug 모듈로 정의 됨
`name: Test roles`
  `hosts: all`
  `gather_facts: true`
  `tasks:`
    ``- name: print facts`
      `debug:`
       `var:`
          `ansible_facts`

# Command
`ansible-playbook -i targets1909.yaml scripts/debug_print_fact_vtype.yaml`

# Result
gather_facts로 얻을 수 있는 정보가 모두 출력 됨

# Reference
[js yang]
