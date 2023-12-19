1. 따로 지정을 하지 않는 이상 `master` 브랜치에 계속 커밋이 된다.
2. 별도의 기능 개발이 필요한 경우 `master` 브랜치에서 작업하는 것이 아니라 새로운 브랜치를 생성해 작업한다.
3. 새로운 기능이 완성되면 `master` 브랜치에 `merge`시킨다.

>branch 생성 및 이동
```shell
git branch testing # testing이라는 branch 생성

git checkout testing # testing branch로 이동
git switch testing # testing branch로 이동

git checkout -b testing # testing branch 생성 + 이동
git switch -C testing # testing branch 생성 + 이동
```

>branch 관리
```shell
git branch # branch 목록
git branch -r # 원격저장소 branch 목록
git branch --all # 원격저장소 branch가 포함된 목록
git branch -v # branch 별로 마지막 commit 내역

git branch --merged # merge된 branch 목록
git branch --no-merged # merge가 안된 branch 목록

git branch -d testing # testing이라는 이름을 가진 branch를 삭제
git push origin --delete testing # testing branch 삭제 내역을 원격저장소 sync

git branch --move testing testingVersion # branch명 변경
git push --set-upstream origin testingVersion # branch명 변경사항 원격저장소 sync
```