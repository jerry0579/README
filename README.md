top : 실시간 프로세스 출력
>top은 버전별로 실행 가능한 명령어에 차이가 있을 수 있습니다. top-v를 통해 top 버전을 확인할 수 있습니다. 아무 옵션을 주지 않은 top을 입력하면 상단과 하단의 두 개의 영역으로 구분되어 내용이 표시됩니다. 상단에는 시스템에 대한 전반적인 요약 정보가, 하단에는 프로세스별 구체적인 정보가 표기됩니다. 정보는 3초마다 업데이트됩니다.
#
>상단의 첫번째 줄(top -)은 왼쪽부터 순서대로 현재 시간, 컴퓨터가 연속으로 실행되고 있는 시간, 로그인 한 사용자 수, 로드 에버리지(load average)를 보여줍니다. 로드 에버리지는 숫자가 3개인데, 차례로 1분, 5분, 15분 간의 로드의 평균을 나타냅니다. 로드란 리소스 사용량을 비율로 표시한 지표를 의미하는데요.
싱글 코어일 때 1.0이면 100%를 모두 사용하고 있다는 의미입니다. 2코어에 1.0이면 50%를 사용하고 있다는 것입니다.

>두번째 줄(task)은 프로세스의 상태를 표시합니다. 순서대로 총 프로세스 수, 실행되고 있는 프로세스 수, 대기 중인 프로세스 수, 멈춘 프로세스 수, 좀비 상태인 프로세스 수를 의미합니다.

>세번째 줄(Cpu)은 CPU 사용 정보를 나타냅니다. 아래 정보에 따라 각각 비율이 표기됩니다. 
>네번째 줄(Mem)은 물리 메모리 사용 정보를 나타냅니다. 그 뒤로는 순서대로 총 메모리(total), 여유 메모리(free), 사용 중인 메모리(used), 버퍼 또는 캐시 메모리(buff/cache)를 의미합니다.

>다섯번째 줄(Swap)은 스왑 메모리 정보를 나타냅니다. 표기 방식은 물리 메모리와 동일합니다. 스왑 메모리는 가상 메모리로 불리며, 메모리가 부족할 때 디스크 공간을 이용해서 부족한 메모리 공간을 대체할 수 있는 메모리입니다. 
때문에 물리 메모리가 가득 차도 스왑 메모리에 여유가 있으면 프로세스를 구동할 수 있습니다.
```
1.  us : 사용자 영역 프로세스에서의 CPU 사용률입니다.
2.  sy : 커널 영역 프로세스에서의 CPU 사용률입니다.
3.  ni : 우선순위로 할당된 사용자 영역 프로세스를 실행하는데 소요되는 CPU 사용률입니다.
4.  id : CPU를 사용하고 있지 않은 비율입니다.
5.  wa : I/O가 완료될 때까지 기다리는 CPU 사용률입니다.
6.  hi : 하드웨어 인터럽트에 사용되는 CPU 사용률
7.  si : 소프트웨어 인터럽트에 사용되는 CPU 사용률
8.  st : CPU를 가상 머신에서 사용함으로써 생기는 손실된 CPU의 비율
```
하단 정보
하단에는 프로세스 목록과 각 프로세스별 정보가 표기됩니다.
```
1.  PID : 프로세스 ID입니다.
2.  USER : 프로세스의 소유 계정입니다.
3.  PR : 프로세스 우선순위입니다.
4.  NI : PR에 영향을 주는 나이스 값입니다.
5.  VIRT : 프로세스가 사용하고 있는 가상 메모리의 총량입니다.
6.  RES : 프로세스가 사용하고 있는 물리 메모리의 양입니다.
7.  SHR : 다른 프로세스와의 공유 메모리입니다.
8.  S : 프로세스의 상태를 의미합니다. D는 네트워크 I/O를 대기하고 있는 상태, R은 실행 중인 상태, S는 대기 상태, Z는 좀비 상태입니다. 좀비 상태란 부모 프로세스가 죽은 자식 프로세스를 의미합니다.
9.  %CPU : 프로세스의 CPU 사용률입니다.
10.  %MEM : 프로세스의 물리 메모리 사용률입니다.
11.  TIME+ : 100초 안에 사용하는 CPU 사용량입니다.
12.  COMMAND : 명령줄입니다.
```  
ps : 프로세스 출력
>리눅스는 다중 사용자, 사용 작업 시스템이기 때문에 여러 개의 프로세스를 동시에 수행하기 때문에 항상 어떤 프로세스들이 실행되고 있는지 모니터링할 필요가 있습니다.
따라서 현재 시스템에서 실행 중인 프로세스에 관한 정보를 출력하여 사용자에게 정보를 제공하는 명령어가 필요한데 이때 사용하는 명령어가 ps입니다.
윈도우에서 특정 프로세스가 실행 중인지 확인하거나 강제 종료하기 위해 작업 관리자를 사용하듯이, 리눅스에서는 ps 명령어가 자주 사용된다.
특히 GUI를 사용하지 않는 서버 환경에서는 대부분의 프로세스들이 백그라운드에서 동작하기 때문에 특정 프로세스가 동작 중인지 확인하기 위해서 많이 쓰인다.
#
1. 기본 프로세스 출력
```
1. a : 터미널과 연관된 프로세스만 출력
2. x : 터미널과 연관되지 않는 프로세스만 출력
3. -A : 모든 프로세스 출력 (-e와 동일)
4. -e : 모든 프로세스 출력
5. -a : 세션 리더와 커미널과 연관되지 않은 프로세스를 제외하고 모든 프로세스를 출력
```
2. 지정한 프로세스 출력
```
1. p : 지정한 PID 목록의 정보만 출력
2. -C : 지정한 프로세스의 실행 파일 이름의 정보만 출력
3. -u : 특정 사용자의 프로세스 정보를 출력
```
3. 프로세스 표시 형식
```
1. u : 프로세스의 소유자 정보를 함께 출력
2. l : BSD 형식의 긴 형식으로 출력
3. e : 프로세스 정보와 함께 프로세스의 환경변수 정보도 출력
4. -l : 긴 포맷으로 출력
5. -o : 사용자 정의 형식 지정 가능
```
4. 프로세스 장식
```
1. f : 프로세스 계층을 텍스트 형식의 트리구조를 보여줌.
2. -f : 전체 포맷으로 출력
```
jobs :현재 세션의 작업 상태를 출력한다.
#
>jobs는 작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경되었지만 보고되지 않은 상태 등을 표시한다.
 
kill :시그널 - 프로세스 종료
#
>시그널은 프로세스 사이의 통신 수단인데 어떤 프로세스에 메시지를 보내 프로세스를 제어한다.
명령어를 실행함으로써 프로세스가 시작되고 그 프로세를 제어하기 위하여 사전에 정의된 시그널이 존재한다.
```
$ kill [options] [pid]
$ kill -9 PID # PID를 시그널 번호 9(KILL) 전송해서 죽임
$ kill -TERM -1 # 자신이 실행한 모든 프로세스를 종료
-signal, -s signal : 지정한 시그널을 보냄
-l :사용 가능한 시그널의 목록을 출력
```
