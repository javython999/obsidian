>git commit

```shell
git commit
```
* staging 파일들을 commit 한다.

>git commit -m "commit message"
```
git commit -m "init"
```
* staging 파일들을 메세지와 함께 commit 한다.

>git commit -am "commit message"
```shell
git commit -am "init"
```
* 모든 staging 파일들을 메세지와 함께 commit 한다.

>git log
```shell
git log
```
* commit log를 보여준다.

>git commit --amend
```shell
git commit --amend -m "corrent message" # 커밋 메세지 수정

git commit --amend # 파일 내용을 잘못 수정후 커밋시 사용
				   # 파일 수정후 해당 명령어 실행
```
* 단, 원격저장소에 저장전에만 사용가능하다.