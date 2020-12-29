# 03. Git Remote

- `git remote` : Remote Repository 주소 등록(GitHub Repo)

  - `git remote add origin (주소)` : Remote Repo의 주소를 origin이라는 별칭으로 등록 

  - `git remote -v`  : 등록된 Remote 주소 확인 

    ```
    origin  https://github.com/grace510/my-first-repo.git (fetch)
    origin  https://github.com/grace510/my-first-repo.git (push)
    
    ```

- `git remote(별칭) (브랜치 이름) `: `별칭`으로 `브랜치`를 push (전송)

  - `git push origin main`: origin으로 main 브랜치를 전송 

- `git clone(주소)` : 주소로부터 Repo 가져오기

- `git pull (별칭) (브랜드이름)`: `별칭` 으로부터 `브랜치`를 pull(내려받기)