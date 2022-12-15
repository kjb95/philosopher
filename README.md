## 식사하는 철학자 문제

## 프로젝트 실행 방법

1. 프로젝트 디렉토리에 들어가기  
   ex): `cd philo_one`
2. makefile의 명령어 `make`를 실행하여 c파일들 컴파일 하기
3. 인자를 포함하여 프로그램 실행시키기  
   ex) `./philo_one 4 800 100 200`  
   `4`: 철학자수=포크의수  
   `800`: 철학자가 밥을먹지않고 버틸수 있는 시간  
   `100`: 철학자가 밥먹는데 걸리는시간  
   `200`: 철학자가 잠자는데 걸리는 시간

## 프로젝트 목표

deadlock 문제를 해결하여 철학자가 굶어죽지 않도록 만들기

## 프로젝트 설명

쓰레드가 자원을 공유하는 상황을 구현 했고, 그 상황은 아래와 같습니다.  
n명의 철학자는 원형 식탁에서 식사를 하며, 각 철학자 사이에는 포크가 하나씩 놓여 있습니다. (따라서 포크는 n개 입니다.)  
철학자가 식사를 하기 위해서는 철학자 양 옆에 존재하는 포크를 하나씩 모두 잡아야 식사를 할 수 있습니다.  
철학자들은 다음의 과정을 통해 식사를 합니다.

1. 일정 시간 생각을 한다.
2. 양쪽의 포크를 잡으면 일정 시간만큼 식사를 한다.
3. 양쪽의 포크를 내려놓는다.
4. 다시 1번으로 돌아간다.

자원을 공유하는 과정에서 교착상태와 기아상태가가 발생합니다.  
교착상태 : 우연히 모든 철학자들이 자기 왼쪽 포크를 잡고 있다면, 모든 철학자들이 자기 오른쪽의 포크가 사용 가능해질 때까지 기다려야 합니다.  
기아상태 : 결국, 포크를 사용할때까지 기다리다가 모든 철학자는 양쪽 포크를 잡지 못하고 아무것도 진행할 수 없는 상태가 됩니다.

## 프로젝트 문제 해결

pthread_create()로 쓰레드 또는 fork()로 프로세스(철학자) 를 생성하고, 자원(포크)을 공유하는 상황을 구현했습니다.  
뮤텍스 또는 세마포어를 이용하여 교착상태와 기아상태를 해결 했습니다.

## philo_one

각 철학자는 쓰레드 입니다.  
포크의 상태를 뮤텍스로 관리합니다.

## philo_two

각 철학자는 쓰레드 입니다.  
포크의 상태를 세마포어로 관리합니다.

## philo_three

각 철학자는 프로세스 입니다.  
포크의 상태를 세마포어로 관리합니다.