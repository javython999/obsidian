>git log
```shell
git log
```
* 로그를 보여준다.

>git log -p
```shell
git log -p
```
* 수정된 파일들의 내용도 보여준다.

>git log --oneline
```shell
git log --online
```
* 로그를 커밋 해시코드, 커밋 메세지 형태로 한 줄로 보여준다. 

>git log --pretty=옵션
```shell
git log --pretty=oneline
git log --pretty=format:"%h %an %ar %s"  #해시코드, 작업자명, 작업시간, 타이틀
```
* 로그를 원하는 포맷으로 출력 할 수 있다. 
* 사용할 수 있는 포맷은 https://git-scm.com/docs/git-log 참고

>git log -숫자
```sheel
git log -3
```
* 최근 3개의 로그를 보여준다.

>git log --grep="찾을 단어"
```shell
git log --grep="project"
```
* --grep="찾을 단어" 옵션을 주면 찾을 단어가 포함된 log를 보여준다.

> git log -S "찾을 단어" -p
```shell
git log -S "about" -p
```
* 소스코드(컨텐츠)안의 내용중에서 찾고 싶은 경우 사용한다.

>git log 파일명
```shell
git log about.txt
```
* 해당 파일에 관한 로그만 보여준다.

>git show 해시코드
```shell
git show ad32Dge
```
* show 커밋 해시코드를 사용하면 해당 커밋에 대해 로그를 보여준다.