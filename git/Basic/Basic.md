> git 초기화
```shell
git init
```
현재 디렉토리를 git repository로 초기화 한다.

>git 제거
```shell
rm -rf .git\
```
.git 폴더를 삭제해서 git을 제거 한다.

> git status
```shell
git status
```
현재 파일들의 상태를 확인할 수 있다.

> git add
```shell
git add a.txt
```
해당 파일을 staging으로 보낸다.

>git rm --cached a.txt
```shell
git rm --cached a.txt
```
해당 파일을 staging에서 untracked로 보낸다.

>.gitignore 파일
```shell
.gitignore파일을 생성하고 
이 파일안에 tracked 대상에서 제외하고 싶은 파일들을 기술해주면
깃이 관리하는 파일에서 제외시킬 수 있다.
```

