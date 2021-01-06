# 08. Merge Branch

### 방식 ###

Merge는 Main(Master) branch에서 해주는 것. 각기 다른 branch 진행사항을 Main(Master)로 끌고오는 것. 권한 자체가 Main(Master)에 있음

`git branch [브랜치 이름]` : 브랜치 생성. 가지쳐나오는 뿌리 중요! 어디서부터 갈라져나오는 것인지 주의해서 설정 

`git merge [브랜치 이름]`



1. Fast-Forward : 한쪽 브랜치는 진행된거 없는 동안  다른 쪽 브랜치에서 진행된 것을 별 다른 절차없이 끌고와서 합쳐줌. 이후 해당 곁다리 브랜치 제거 `git branch -d [브랜치 이름]`

   ```
   源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~ (login)
   $ git log --oneline --graph --all
   * 040a9ff (HEAD -> login) login added
   * 12102e2 (master) b added
   * db16b06 a added
   
   源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~ (master)
   $ git merge login
   Updating 12102e2..040a9ff
   Fast-forward
    login.txt | 0
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 login.txt
   
   源▒▒▒삙@LAPTOP-D732RQ5Q MINGW64 ~ (master)
   $ git branch -d login
   Deleted branch login (was 040a9ff).
   ```

   

2. 3-Way merge : 최신 버전을 pull 받지 않은 상태로 진행하였을때, 해당 진행상황을 master로 끌고옴. Merge 메시지 남겨짐. 파일 변경 없고 충돌도 없음. 기록을 위한 commit.

   ```
   $ git log --oneline --graph --all
   * cd5d18b (HEAD -> logout) logout added
   | * e5f8796 (master) main added
   |/
   * 040a9ff login added
   * 12102e2 b added
   * db16b06 a added
   
   
   $ git merge logout
   
   
   $ git log --oneline --graph --all
   *   9052153 (HEAD -> master) Merge branch 'logout'
   |\
   | * cd5d18b (logout) logout added
   * | e5f8796 main added
   |/
   * 040a9ff login added
   * 12102e2 b added
   * db16b06 a added
   
   ```

   

3. Merge Conflict : 서로 다른 브랜치에서 동일한 파일 각자 건드려서 해당 파일에 대한 충돌생긴경우.       -> 사용자가 지정하여 합의를 해야함 

   깃허브: Pull requests 항목에 뜨게됨

   로컬 깃: editor창에 각 브랜치에서의 change 보여주고, 직접 수정. 둘중 하나를 선택하거나 둘다 반영한 방법으로 작성

