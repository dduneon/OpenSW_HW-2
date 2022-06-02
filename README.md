# 📝 조사내용 README파일로 정리하기

### 20184366 김준현

<br>

# 목차

1. 리눅스 명령어 조사하기
   - `top` , `ps` , `jobs` , `kill`
2. vim 에디터 매크로 사용방법 조사하기

<br>

# 1. 리눅스 명령어 조사하기

# ✏️ `top`

<br>

`top` 명령어는 현재 OS의 상태를 나타내주는 명령어로, 메모리 사용량, CPU 사용량 등을 나타내주며 `top`을 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여줍니다.

리눅스에서 `top` 명령어를 실행하면 다음과 같이 노출되는데, 위에는 전체의 **요약** 이 있고, 아래에는 각 프로세스마다 구체적인 내용을 포함하고 있습니다.

<img width="564" alt="image" src="https://user-images.githubusercontent.com/84072084/171211499-f1195c61-c921-44c1-b303-cd9727f852c2.png">

<br>

이 `top`명령어를 보면, 위 영역과 아래 영역이 공백 한 줄로 구분되어 있음을 알 수 있는데 윗줄을 **요약 영역**이라고 부릅니다.

<img width="575" alt="dd" src="https://user-images.githubusercontent.com/84072084/171213835-e082a783-f8dc-428e-b181-c70278ab0d61.png">

<br>

**요약 영역**의 여러 부분을 다음과 같이 나누어 보았습니다.

| System time | Uptime | User | Load Average |
|--|--|--|--|
| Tasks | - | - | - |
| CPU | - | - | -|
| Memory | - | - | - |
| Memory | - | - | - |

<br>

## Tasks

*현재 프로세스들의 상태를 나타내줍니다.*

- `Total` : 전체 프로세스 수

- `Running` : Running 상태인 프로세스 수

- `Sleeping` : 대기상태인 프로세스 수 

- `Stopped` : 종료된 프로세스 수

- `zombies` : 좀비 상태인 프로세스 수

<img width="575" alt="dd" src="https://user-images.githubusercontent.com/84072084/171214953-65d77435-342a-4050-a214-70a91509af55.png">

<br>

## CPU

*CPU가 어떻게 사용되고 있는지 그 사용율을 보여주는 영역*

- `us` : 프로세스의 유저 영역에서의 CPU 사용률

- `sy` : 프로세스의 커널 영역에서의 CPU 사용률

- `ni` : 프로세스의 우선순위(priority) 설정에 사용하는 CPU 사용률

- `id` : 사용하고 있지 않는 비율

- `wa` : IO가 완료될때까지 기다리고 있는 CPU 비율

- `hi` : 하드웨어 인터럽트에 사용되는 CPU 사용률

- `si` : 소프트웨어 인터럽트에 사용되는 CPU 사용률

- `st` : CPU를 VM에서 사용하여 대기하는 CPU 비율

<br>

## Memory

*메모리와 관련된 영역*

- `total` : 총 메모리 양

- `free` : 사용 가능한 메모리 양

- `used` : 사용중인 메모리 양

<br>

## 디테일 영역

*각 프로세스에 대한 상세한 내용을 나타냄*

<img width="557" alt="image" src="https://user-images.githubusercontent.com/84072084/171218423-b0196ec4-4719-4257-88b0-5173aad04bd2.png">

- `PID` : Process ID, 프로세스를 구분하기 위한 겹치지 않는 고유한 값

- `USER` : 해당 프로세스를 실행한 USER이름 또는 효과를 받는 USER의 이름

- `PR` : 커널에 의해서 스케줄링되는 우선순위

- `NI` : PR에 영향을 주는 값

- `VIRT` : 프로세스가 소비하고 있는 총 메모리

- `RES` : RAM에서 사용중인 메모리의 크기

- `SHR` : 다른 프로세스와의 공유메모리를 나타냄

- `%MEM` : RAM에서 RES가 차지하는 비율

- `S` : 프로세스의 현재 상태

- `TIME+` : 프로세스가 사용한 토탈 CPU 시간

- `COMMAND` : 해당 프로세스를 실행한 커맨드를 나타냄

<br>

# 유용한 top용 커맨드

## `k` - kill process

top을 통해 프로세스를 모니터링하며 프로세스를 종료할 수 있는 기능

<img width="553" alt="image" src="https://user-images.githubusercontent.com/84072084/171223846-18193257-b1a2-47b8-8129-d959ee8bea07.png">

다음과 같은 화면이 나타나고, `kill` 할 `PID`를 입력해주면 된다.

<br>

## Sorting the process list

디테일 영역에서 원하는 값을 기준으로 정렬하는 방법을 제공

아래 커맨드를 누르면 해당 값을 기준으로 정렬된다.

- `M` : Memory usage를 기준으로 정렬

- `P` : CPU usage를 기준으로 정렬

- `N` : Process ID를 기준으로 정렬

- `T` : Running Time을 기준으로 정렬

- `R` : 오름차순과 내림차순을 변경

<br>


# ✏️ `ps`

`ps`명령어는 프로세스의 현재 상태를 출력하는 명령어로, 기본적인 필드로는 **PID, TTY, TIME, CMD** 헤더의 필드와 내용을 출력합니다.

<img width="394" alt="image" src="https://user-images.githubusercontent.com/84072084/171653412-7b3a3e7f-e5b6-4442-a74f-3bc130b321f4.png">

<br>

## 사용 방법
```bash
ps [옵션]
```

<br>

## 사용 예시

`PID`, `CMD` 등 프로세스의 기본적인 내용만 출력 (옵션을 주지 않은경우)
```bash
ps
```

<br>

모든 프로세스를 출력
```bash
ps -e
```

<img width="300" alt="image" src="https://user-images.githubusercontent.com/84072084/171665507-ddcc4d96-525d-4a85-9897-8f80d99c1c33.png">

<br>

풀 포맷으로 출력 (`uid, pid, ppid, tty` 등)
```bash
ps -f
```

<img width="343" alt="image" src="https://user-images.githubusercontent.com/84072084/171665602-8af21821-1066-4546-91e5-72963b230f4d.png">

<br>

긴 포맷으로 출력 (풀 포맷 + `F, S, PRI` 등)
```bash
ps -l
```

<img width="422" alt="image" src="https://user-images.githubusercontent.com/84072084/171665763-901afaa3-9df0-4763-b94f-945805e39cdf.png">

<br>

프로세스 번호(`PID`)가 1인 프로세스를 출력
```bash
ps -p 1
```

<img width="405" alt="image" src="https://user-images.githubusercontent.com/84072084/171665902-fc9d56b5-d5ad-4087-96c8-2931fabf94cb.png">

<br>

계정이 seek인 프로세스를 출력
```bash
ps -u seek
```

<img width="530" alt="image" src="https://user-images.githubusercontent.com/84072084/171663799-3d6149c8-e248-471c-9f74-9e2963f062a8.png">

<br>

모든 프로세스를 플 포맷으로 출력, `more` 명령어를 이용하여 페이지 단위 출력
```bash
ps -ef | more
```

<img width="346" alt="image" src="https://user-images.githubusercontent.com/84072084/171664142-4fda92c9-77b3-4340-8a9c-5d3499c33959.png">

<br>

모든 프로세스를 풀 포맷으로 출력한 목록에서 `grep`을 이용해 seek이 포함된 행을 출력

```bash
ps -ef | grep seek
```

<br>

## 여러 필드들

| 필드 명 | 설명 | 옵션 |
|--|--|--|
| ADDR | 프로세스 스택의 세그먼트 번호 | -l, l |
| BND | 커널 스레드가 바인드되는 프로세스의 논리 프로세스 번호 | -o |
| C | 프로세스 사용량 | -f, -l, l |
| CMD | 사용자가 실행한 명령 이름 | -f, -l, l |
| COMMAND | 사용자가 실행한 명령 이름 | s, u, v |
| F | 프로세스 및 스레드에 관련된 항목 | -l, l 력
| LIM | 메모리에 대한 소프트 한계와 관련된 항목 | v |
| NI | 프로세스의 우선순위 값. 낮을수록 CPU시간이 높다 | -l, l |
| PID | 프로세스 ID | 기본 필드 |
| PRI | 프로세스 스케줄링 우선순위. 낮을 수록 우선순위가 높다 | -l, l |
| RSS | 프로세스의 실제 메모리의 크기(KB) | -l, l |
| S | 프로세스나 커널 스레드의 상태 | -l, l |
| SIZE | 가상 이미지의 크기 | v |
| SAT | 실행되고 있는 프로세스의 상태 | s, u, v |
| STIME | 프로세스의 시작 시간 | -f, u |
| SZ | 프로세스가 사용하는 자료와 스택의 크기 | -l, l |
| TIME | 프로세스가 소비한 총 시간 | 기본 필드 |
| TRS | 텍스트의 실제 메모리 크기 | v |
| TTY | 연결되어 있는 터미널 | 기본 필드 |
| UID | 사용자 ID | -f, -l, l |
| USER | 사용자 이름 | u |
| WCHAN | 프로세스에 거주하는 커널 함수 | -l, l |

<br>

# ✏️ `jobs`

`jobs` 명령어는 현재 세션의 작업의 상태를 표시하는 명령어이다.

현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되며, 각 작업에는 번호가 붙어 있어 `kill` 명령어 뒤에는 '%번호' 등으로 사용할 수 있다.

<br>

```bash
jobs [option] [num]
```

`jobs` 명령어는 현재 쉘 프로세스의 자식 백그라운드 프로세스를 보여준다고 생각하면 된다.

<img width="486" alt="image" src="https://user-images.githubusercontent.com/84072084/171668463-f7a8ee5e-9cbb-474e-aa3d-60324255a131.png">

<br>

## 상태값

| 상태 | 설명 |
|--|--|
| Running | 작업이 계속 진행중임 |
| Done | 작업이 완료되어 0을 반환 |
| Done(code) | 작업이 종료되었으며 0이 아닌 코드를 반환 |
| Stopped | 작업이 일시 중단 |
| Stopped(SIGTSTP) | SIGSTP 시그널이 작업을 일시 중단 |
| Stopped(SIGSTOP) | SIGSTOP 시그널이 작업을 일시 중단 |
| Stopped(SIGTTIN) | SIGTTIN 시그널이 작업을 일시 중단 |
| Stopped(SIGTTOU) | SIGTTOU 시그널이 작업을 일시 중단 |

<br>

## 옵션

| 옵션 | 설명 |
|--|--|
| -l | 프로세스 그룹 ID를 state 필드 앞에 출력 |
| -n | 프로세스 그룹 중에 대표 프로세스 ID를 출력 |
| -p | 각 프로세스 ID에 대해 한 행씩 출력 |
| command | 지정한 명령어를 실행 |

<br>

<img width="476" alt="image" src="https://user-images.githubusercontent.com/84072084/171671235-129a732a-46b8-4a8b-a968-8c8b2be2fa9b.png">

- `-l` 옵션은 `state` 필드 앞에 프로세스 ID를 출력한다

<br>

<img width="448" alt="image" src="https://user-images.githubusercontent.com/84072084/171671905-718c7713-a199-4938-bd9b-e21508229caa.png">

- `-p` 옵션은 % 뒤에 나오는 문자로 시작하는 모든 프로세스 ID를 확인할 수 있다

<br>

# ✏️ `kill`

프로세스에 특정한 SIGNAL을 보내는 명령어로, 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 사용한다.

```bash
kill [pid]
```

일반적으로 위와 같은 방법으로 죽이려는 프로세스의 `pid`를 얻은 다음, kill 명령어의 인자로 넘기면 된다.

<br>

## 사용자 지정 시그널 전송

```
kill -s [signal] [pid]
```

kill 명령어의 default 시그널은 TERM(15) 인데, `-s` 옵션을 주면 다른 시그널을 보낼 수 있다.

예를 들어, 프로세스가 TERM(15) 시그널에 응답하지 않으면 다음의 명령어처럼 KILL(9)를 사용하여 강제로 죽일 수 있다.

<img width="447" alt="image" src="https://user-images.githubusercontent.com/84072084/171674940-036a6503-c46a-45c6-b052-2fb483dd8078.png">

`PID` 9를 가지는 bash를 `kill` 하기 위하여 `kill 9` 를 명령하였는데, 아무런 응답이 없었다.

여기에서 `kill -s KILL 9` 를 통하여 `SIGKILL` 시그널을 전송하였더니 bash의 프로세스가 종료됨을 볼 수 있었다.

`kill -9 9` 명령으로도 동일하게 작동시킬 수 있다.

> `SIGKILL = KILL = 9`

<br>

## 시그널의 종류

<img width="474" alt="image" src="https://user-images.githubusercontent.com/84072084/171675416-eb9d48ae-7c99-433b-a19c-6cbb8bc43844.png">

프로세스는 대부분의 시그널을 무시할 수 있지만, `9(SIGKILL)`과 `19(SIGSTOP)` 시그널은 무시할 수 없다.

<br>

# 2. vim에디터 매크로 사용방법 조사하기



# Reference

[https://www.booleanworld.com/guide-linux-top-command/](https://www.booleanworld.com/guide-linux-top-command/)

[https://terms.naver.com/entry.naver?docId=4125682&cid=59321&categoryId=59321](https://terms.naver.com/entry.naver?docId=4125682&cid=59321&categoryId=59321)
