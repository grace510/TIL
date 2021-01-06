# 04.Git Push Error

```bash
To https://github.com/grace510/TIL-test.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/grace510/TIL-test.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

**the remote contains work that you do not have locally** : 깃허브로부터 pull 안하고 수정사항 만들어 push해서 발생한 핵심 이슈



**해결** :pull 을 통해 통합(재정렬)시켜놓는 것이 필요

`git pull origin master`

->Merge made by the 'recursive' strategy.

git log --graph 를 통해 merged 시각적으로 확인할 수 있음

```bash
$ git log --oneline --graph
*   e2ab7ad (HEAD -> master, origin/master, origin/HEAD) Merge branch 'master' of https://github.com/grace510/TIL-test
|\
| * 9ebaaad d.txt added
* | f9bb953 e.txt added
|/
* 7a9d497 b.txt added
* 3a4a19d a.txt added

```

