# 06. gitignore

- 우리가 git으로 관리하고 싶지 않은 파일들을 제외시키는 방법

  - 원치 않는 파일 제외. 관리 필요없는 dummy 파일 (Thumbs.db, .DS_store 등등)
  - 외부에 공개되면 안되는 것들(key, secret)

- `.gitignore`

  - `.gitignore`에 작성된 파일들은 git으로 관리하지 않고 무시
  - Atom, VScode 등의 에디터와 연동이 되어 Untracked파일, Modified파일 색으로 표시됨

  - 작성법

    ```
    f.txt # 특정파일
    secret/ #특정 폴더. 해당 폴더 하위에 있는 모든것들 다 제외됨
    *.png # 특정확장자 전부. 모든 png 제외
    !profile.png # profile.png만 예외적으로 포함시켜주기
    ```

  - commit관리 들어가기 전 아주 처음부터 `.gitignore`관리를 해주어야 함

    - 이미 commit 경력이 있는 파일은 `.gitignore`에 넣어줘도 제외처리 안됨

    - 그렇다면 이미 commit을 한 파일들은 어떻게 관리?

      ​	1.`.gitignore`에 파일 명시

      2. `git rm --cached [파일명]` : 

         - git에서 더이상 관리하지 않겠다. 

         - WD에서 삭제되었기 때문에 더이상 관리대상이 아님

           ```bash
           $ git rm --cached g.txt
           rm 'g.txt'
           
           源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
           $ ls
           TIL-test/  a.txt  b.txt  d.txt  e.txt  f.txt  g.txt  h.txt
           
           源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
           $ git status
           On branch master
           Changes to be committed:
             (use "git restore --staged <file>..." to unstage)
                   deleted:    g.txt
           
           ```

           

         -  git status 상에서는 삭제 처리이지만 ls에는 g.txt그대로 있다.

         - 따라서 g.txt가 있던 이전 commit 으로 돌아가면 g.txt가 그대로 있다.

         - 

