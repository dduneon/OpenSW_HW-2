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

**요약 영역**의 여러 부분을 다음과 같이 나누어 보았습니다.

| System time(시스템 현재시간) | Uptime(OS가 살아있는 시간) | User(유저 세션수) | Load Average(CPU가 수행하는 작업의 양 평균) |
|--|--|--|--|
| Tasks |
| CPU |
| Memory |
| Memory |

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

<br>

# ✏️ `jobs`

<br>

# ✏️ `kill`

<br>

# Reference

[https://www.booleanworld.com/guide-linux-top-command/](https://www.booleanworld.com/guide-linux-top-command/)

