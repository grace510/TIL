# 05. Git 명령 취소하기

1. git add 취소하기

   - git add가 된 상황

     ```bash
     $ git status
     On branch master
     Changes to be committed:
       (use "git restore --staged <file>..." to unstage)
             new file:   f.txt
     ```

   - `git restore staged f.txt` :add 실행 취소

     ```bash
     $ git status
     On branch master
     Untracked files:
       (use "git add <file>..." to include in what will be committed)
             f.txt
     
     ```

     ​		구버전의 경우 `$ git reset HEAD f.txt`

2. git commit 취소 (되돌아가기)

   ```
   $ git reset [돌아가고자 하는 지점인 commit의 hash(노란색) ]
   ```

   ```
   $ git log --oneline
   ae30af1 (HEAD -> master) f added
   e2ab7ad (origin/master) Merge branch 'master' of https://github.com/grace510/TIL-test
   f9bb953 e.txt added
   9ebaaad d.txt added
   7a9d497 b.txt added
   3a4a19d a.txt added
   ```

   ```
   $ git reset e2ab7ad
   
   $ git log --oneline
   e2ab7ad (HEAD -> master, origin/master) Merge branch 'master' of https://github.com/grace510/TIL-test
   f9bb953 e.txt added
   9ebaaad d.txt added
   7a9d497 b.txt added
   3a4a19d a.txt added
   ```

   - ls 했을 때 f.txt 안보임

     

   - 옵션

     ```
     $ git reset --mixed [hash]
     ```

     ​	staging 없어짐(git add 취소) +  작업한 것 남아있음. 따로 --mixed 안해도 default로 적용됨

     ```
     $ git reset --soft [hash]
     ```

     ​	staging 그대로 유지됨 (git add 유지)+ 작업한 것 남아있음

     ```
     $git reset --hard [hash]
     ```

     ​	***주의:작업한것 복구 불가하게 완전 삭제***

   - hash

     - `git log --oneline`하면 노란색 7자리 숫자,알파벳. 그냥 `git log`하면 기다란 난수

   - HEAD의 상대적 위치: hash값 없이 상대적 위치만으로 이전에 쌓인 commit으로 갈 수 있음

     - HEAD~{숫자} : 현재로부서 "숫자"번째만큼 이전의 commit 단계로 돌아감

       - HEAD~1
       - HEAD~2

       ```bash
       源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
       $ git log --oneline
       3d9fd4c (HEAD -> master) h added
       1a98433 g added
       13243c4 f added
       e2ab7ad (origin/master) Merge branch 'master' of https://github.com/grace510/TIL-test
       f9bb953 e.txt added
       9ebaaad d.txt added
       7a9d497 b.txt added
       3a4a19d a.txt added
       
       源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
       $ git reset HEAD~1
       
       源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
       $ git log --oneline
       1a98433 (HEAD -> master) g added
       13243c4 f added
       e2ab7ad (origin/master) Merge branch 'master' of https://github.com/grace510/TIL-test
       f9bb953 e.txt added
       9ebaaad d.txt added
       7a9d497 b.txt added
       3a4a19d a.txt added
       
       $ git status
       Untracked files:
         (use "git add <file>..." to include in what will be committed)
               h.txt
       
       ```

   - git log시 내용이 너무 많아 잘리는 경우

     - q로 종료

3. WD(Working Directory) 변경 내용 취소, 삭제하기 == 원상복구. 실수로 뭔가를 삭제했을때 해당 파일 다시 복구할 수 있음

   - WD
     - 현재 작업중인 공간 
     - == Git이 관리하고 있는 공간
     - == 한번이라도 commit 기록된 파일들이 있는 공간(staging 되어 있는 파일)
   - `$ git restore [파일명]`

   ```bash
   ------------------------------------
   $ rm a.txt
   
   源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
   $ git status
   On branch master
   Changes not staged for commit:
     (use "git add/rm <file>..." to update what will be committed)
     (use "git restore <file>..." to discard changes in working directory)
           deleted:    a.txt   (-> a.txt 삭제)
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           h.txt
   
   
   -------------------------------------
   $ git restore a.txt
   
   源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
   $ git status
   On branch master
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           h.txt
   
   nothing added to commit but untracked files present (use "git add" to track)
   
   源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~/lectureroom (master)
   $ ls
   TIL-test/  a.txt  b.txt  d.txt  e.txt  f.txt  g.txt  h.txt   
   -> 삭제됐던 a.txt 다시 등장 
   
   ```

   