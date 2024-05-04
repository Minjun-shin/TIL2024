# Docker Command
### `run`
```Shell
$ docker run imagename
```
- nginx, ubuntu 등
- 처음으로 실행할 경우 Docker hub에서 해당 이미지를 가져옴
- 공식에서 제공하는 이미지가 아니면 추가적인 라이브러리 명 필요
### `ps`
```Shell
$ docker ps
```
- 실행 중인 컨테이너 정보 가져옴
- ID, 이름, 명령어, 이미지, 포트번호 등
- `-a`옵션 사용 시 종료한 컨테이너 등을 포함해서 전부 표시
### `stop`
```Shell
$ docker stop 컨테이너 이름 또는 ID
```
- 해당 컨테이너 종료
### `remove`
```Shell
$ docker rm 컨테이너 이름 또는 ID
```
- 해당 컨테이너 제거
### `images`
```Shell
$ docker images
```
- 사용 가능 이미지 정보 목록 출력
- ID, 사이즈, 태그 등 포함
### `rmi`
```Shell
$ docker rmi imagename
```
- 해당 이미지 삭제
- 해당 이미지를 사용하는 컨테이너 모두 종료 후 삭제해야 함
### `pull`
```Shell
$ docker pull imagename
```
- 컨테이너 실행 없이 해당 이미지 가져오기
### ubuntu 이미지로 실행 시 바로 종료되는 이유
- 컨테이너의 목적이 특정 작업이나 프로세스를 처리하는 것이기 때문
- ubuntu는 단순히 다른 앱의 베이스가 되는 운영 체제 이미지이기 때문에 실행되는 프로세스가 없기 때문
- Append command
  - run 명령어에 추가적인 명령어를 덧붙여 프로세스를 덧붙일 수 있음 예시) sleep 5
### `exec`
```
docker exec container_name command
```
- 이미 실행 중인 컨테이너에서 실행할 명령어를 입력
### attach & detach
- kodekloud/simple-webapp
  - 8080 포트에서 신호를 수신하는 간단한 웹서버 이미지
- attach
  - 일반적인 run 명령어로 실행 시 연결 모드로 실행
  - 실행 중인 동안 입력 불가
- detach
  - `-d` 옵션으로 실행 시 분리 모드로 실행
  - 프롬프트 사용 가능
  - 밑의 명령어로 연결 모드로 변경 가능
  ```
  docker attach 컨테이너_ID_or_Name
  ```
