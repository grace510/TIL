# 01.Git

- `git status`: git으로 관리되고 있는 폴더 (==Repository, 저장소)의 상태를 보여줌

- `git init`: 현재 폴더를 git으로 관리하겠다는 초기화 선언

- `git add` : git으로 관리할 파일들을 추가

  - `git add A.txt` : `A.txt`파일을 INDEX(staging 영역)에 등록
  - `git add .`: `.`(현재폴더)를 INDEX에 등록. 내부의 모든 파일과 경로가 한번에 등록됨

- `git commit`: INDEX에 있는 파일들을 가지고 commit(history, 역사, 기록)을 남김

  - `git commit -m '메세지'` : 기록을 남기면서 `메시지`를 남김(필수)

- `git log`: 남겨온 commit 목록 확인

  - `git log  --oneline --graph`: 그래프, 한줄 기록 조회

- `git config` : git 프로그램의 설정 담당

  ```
  git config --global user.email '이메일주소'
  git config --gloabl user.name '이름'
  ```

  - `git config --global --list`: 현재 git 프로그램에 설정된 값들을 확인

