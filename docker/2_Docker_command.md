# Docker Command
### `run`
```Shell
$ docker run imagename
```
- nginx, ubuntu 등
- 처음으로 실행할 경우 Docker hub에서 해당 이미지를 가져옴
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
- 