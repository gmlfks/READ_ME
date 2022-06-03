# READ_ME
README 과제

-----

## 리눅스 명령어

* **top: 시스템 프로세서, 메모리 사용량과 cpu사용량을 실시간으로 보여줌.**

 (리눅스를 사용하는 디바이스의 성능이나 서버의 기능을 체크할 때 사용함.)
 
 $top(기본 실행 화면)
 
 ![image](https://user-images.githubusercontent.com/104439372/171783640-bb738a32-7ea3-4ba9-aa48-09931db78ff1.png)
 
 현재 서버 시간, 프로세스의 상태, cpu 사용, 메모리 사용 현황등을 보여줌.
 
 top 실행 후 명령어
 
 명령어 | 실행
---------- | ----------------------
shift + p | CPU 사용률이 높은 프로세스 순서대로 표시
shift + m | 메모리 사용률이 높은 프로세스 순서대로 표시
shift + t | 프로세스가 돌아가고 있는 시간 순서대로 표시
 -a       | 메모리 사용량에 따라 정렬
 -n       | 반복되는 횟수를 제한 : -n 숫자
 -u       | 입력한 유저의 프로세스만을 표시 
 숫자 1   | cpu core별로 사용량을 표시
 
 
 
 


* **ps: 현재 실행중인 프로세스를 보여줌.**

$ ps [옵션]

 -A: 모든 프로세서를 출력함.
 
 -u: 특정 사용자의 프로세스 정보를 확인할 때 사용함.(사용자를 지정하지 않으면 현재 사용자를 기준)

 -r: 현재 실행중인 프로세서를 보여줌.

 -i: 프로세스의 상세 내역을 보여줌.

 -ef: 모든 프로세서의 모든 정보를 보여줌. (UID-프로세스 소유자 이름, PID-프로세스 번호 , PPID-부모 프로세스 id, C-cpu 사용률, STIME-프로세스가 시작된 시간,
 TTY-프로세스가 연결된 터미널, TIME-총 cpu사용시간 등 출력)

![캡처 2022-05-28 225108](https://user-images.githubusercontent.com/104439372/170828369-1f05cc53-5fed-40a7-952d-8cf549d28218.png)

 
 $ ps -ef | grep '프로세스명'

* **jobs: 작업의 상태를 표시함.**

(작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 후 보고되지 않은 상태를 표시함. )

![image](https://user-images.githubusercontent.com/104439372/171785211-733ee4a2-bd5c-44c9-9835-fabdc7ebec95.png)


jobs [옵션][job id]

 -l: 프로세스 그룹 id를 state필드 앞에 출력
 
 -n: 프로세스 그룹 중에 대표 프로세스 id를 출력
 
 -p: 각 프로세스 id에 대한 한 행씩 출력
 
 command: 지정한 명령어를 실행
 
 **jobs로 알 수 있는 세션의 상태**
 
 상태 | 설명
--------------- | -------------------------------
Runnig            | 작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중
Done              | 작업이 완료되어 0을 반환하고, 종료된 상태 
Done(code)        | 작업이 정상적으로 완료
 Stopped          | 작업이 일시 중단
 Stopped(SIGTSTP) | SIGTSTP 신호가 작업을 일시 중단
 Stopped(SIGSTOP) | SIGSTOP 신호가 작업을 일시 중단 
 Stopped(SIGTTIN) | SIGTTIN 신호가 작업을 일시 중단
 Stopped(SIGTTOU) | SIGTTOU 신호가 작업을 일시 중단
 
 

* **kill: - 프로세스에 종료 신호를 보냄** 

 (일반적으로 종료되지 않는 프로세스를 안전하게 종료시킬 때 사용함.)

kill [옵션 또는 시그널 번호] PID

$ kill -9 1234

$ kill -SIGKILL 1234

 -l: 시그널의 종류를 출력


![화면 캡처 2022-05-28 210825](https://user-images.githubusercontent.com/104439372/170824905-09bba8e1-2656-4715-af97-b2d5487ad16c.png)

---------

## vim 에디터 매크로

: 매크로->같은 명령어를 반복하는 기능


1. 기본적인 매크로 사용법


- q+a(a키에 recording 시작) -> 반복을 위해 내가 원하는 명령어 동작 -> q(recording 종료)

- @<저장한  매크로 문자>: 특정 문장 저장한 매크로 실행

- 반복횟수@<저장한 매크로 문자>: 매크로 횟수만큼 반복 실행

- @@: 마지막에 수행한 매크로를 실행

2. 자주 사용하는 매크로 등록

- ~/.vimrc를 연다 -> let @a='매크로 문자열'

- 매크로 사용 예시

변경 전

```
package vars

var (
        version string
        Debug bool  
)


```

-----------

변경 후

```
package vars

var (
        //Version TODO
        version string
        //Debug TODO
        Debug bool  
)


```


G(마지막 라인으로 이동) -> **qa(매크로 a시작) -> -O(현재 라인을 다음줄로 밀고 입력 시작)
->//입력 -> ctrl-n(단어 탐색) ->TODO 입력 -> <Esc> -> q(매크로 실행 중지)
 ->a@: 매크로 a실행**
 
 마지막 매크로를 실행하면서 굵게 쓰인 부분이 반복 됨.


