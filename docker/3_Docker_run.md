# Docker Run Additional Options
### 태그
```shell
$ docker run image:tag
```
- docker 이미지에 콜론을 붙이고 작성
- 원하는 버전 등 이미지에 대한 옵션을 고르는 것
- default : `latest`
- docker hub 사이트에서 지원하는 태그들 확인 가능
### stdin
```shell
$ docker run -it image
```
- docker 컨테이너는 표준 입력값을 수신하지 않음 - 비대화형 모드
- `-i`
  - 대화형 모드
  - 호스트의 표준 입력값과 docker 컨테이너를 매핑
- `-t`
  - 컨테이터의 터미널 연결
  - 애플리케이션 프롬프트 출력 표시
### Port mapping
```shell
$ docker run -p host_port:container_port image
```
- 컨테이너들은 기본적으로 자기자신의 포트와 IP를 가지고 있음
- 하지만 이것은 private이기에 docker host에서만 접근 가능
- 따라서 이를 host의 포트와 매핑해야 외부에서 해당 컨테이너로 접근 가능 - `-p` 옵션 사용
- 외부 사용자는 docker host의 IP와 연결된 포트 번호를 사용해서 접근
- 주의 : 하나의 host의 포트에는 두 개 이상의 컨테이너를 연결할 수 없음
### Volume mapping
```shell
$ docker run -v host_dir:container_dir image
```
- 컨테이너를 지웠을 경우 내부에 저장된 데이터도 지워짐
- 이를 방지하기 위해 외부 디렉토리와 매핑
- 위의 명령어에 디렉토리의 경로를 입력
### Inspect
```shell
$ docker inspect container_name_or_id
```
- 컨테이너의 세부정보를 JSON 형태로 나타냄
- 상태, 마운트, 구성 데이터, 네트워크 설정 등
### Log
```shell
$ docker logs container_name_or_id
```
- stdout
- docker 컨테이너의 log 확인