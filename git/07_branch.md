# 07. branch

- branch란? 가지치기

- commit 쌓아가던 중 현재 하던 것을 없애고 이전 commit으로 돌아가는 일은 적을수록 좋다. 

  -> branch로 현재 하던것을 유지하면서 이전 단계로 돌아가 다른 버전으로 다시 진행하기 

- 충돌방지 (ex: 실시간 - 녹화본. 녹화본에 문제 없는지 검토한후 실시간 버전에 적용 )

- 기다릴 필요 없음 (동시간에 서로 다른 branch에서 진행가능. 이후 합병)

- `git branch` : 브랜치 목록 확인

- `git branch [이름]` : `이름` 브랜치 생성

  ```bash
  $ git commit -m 'a added'
  [master (root-commit) b08a647] a added
   1 file changed, 0 insertions(+), 0 deletions(-)
   create mode 100644 a.txt
  
  源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
  $ git branch
  * master
  
  源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
  $ git branch login
  
  源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
  $ git branch
    login
  * master
  
  ```

- `git switch [이름]`: `이름` 브랜치로 이동

  ```bash
  源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
  $ git switch login
  Switched to branch 'login'
  
  源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (login)
  
  ```

  

```bash
源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (login)
$ git log --oneline --graph
* 5a2b11c (HEAD -> login) login added
* b08a647 (master) a added

源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
$ git log --oneline --graph
* b08a647 (HEAD -> master) a added

```

```bash
源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
$ git commit -m 'main txt added'

源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
$ git log --oneline --graph
* f4badd7 (HEAD -> master) main txt added
* b08a647 a added

源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (master)
$ git log --oneline --graph --all  # 한줄로, 그래프포함, 전체 브랜치
* f4badd7 (HEAD -> master) main txt added
| * 5a2b11c (login) login added
|/
* b08a647 a added

```

```bash
源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/git-branch (login)
$ git log --oneline --graph --all
* f4badd7 (master) main txt added
| * 5a2b11c (HEAD -> login) login added
|/
* b08a647 a added
```



- `git switch -c [login]`: 브랜치를 만들면서 바로 해당 브랜치로 이동

  - `git branch [login]` + `git switch [login]` 

  - 구버전: 이동 `git checkout [login]` , 생성하면서 이동 `git checkout -b [login]`