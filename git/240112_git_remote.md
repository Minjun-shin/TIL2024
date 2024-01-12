# Git 원격 저장소


## 원격 저장소에 push

1. 원격 저장소 생성
2. 생성한 저장소를 로컬에 등록
    - `git remote add {별칭} {저장소 URL}`
3. `git push {별칭} {브랜치명}` : 

- 로컬 저장소는 원격저장소와 자동 동기화되지 않는다.
  - 항상 pull하고 작업
  - 추천 - pull -> 작업 -> add -> commit -> push
  


## gitignore란?

- 버전 관리를 하지 않을 파일이나 폴더 및 경로를 등록하는 파일
  - 한 번도 등록되지 않아야 함
  - 따라서 초반에 생성
  - 만약 이미 관리되는 파일일 경우 관리 대상에서 제외
    - `git rm --cached {파일명}`
- gitignore 생성 사이트
  - [gitignore.io](https://www.toptal.com/developers/gitignore)
  - 설정 목록 : 사용언어, 환경, 에디터, 프레임워크
        > 예시 : Python, Visual Studio Code 등등