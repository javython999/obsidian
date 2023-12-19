>git tag 태그
```shell
git tag hello
```
* 현재 head에 태그를 남긴다.

>git tag 태그 해시코드
```shell
git tag hello! 0db3c2f4
```
* 커밋의 해시코드를 입력하면 해당 커밋에 태그를 남긴다.

>git tag 태그 해시코드 -am "자세한 내용"
```shell
git tag hello~ 9bdxc3d23 -am "버그 수정"
```
* 태그와 자세한 메세지를 같이 남길 수 있다.
* 자세한 메세지는 git show 태그이름 명령어 실행시 볼 수 있다.

>git tag -d 태그
```shell
git tag -d hello
```
* 해당 태그를 삭제한다.

>git tag -l "특정 문자"
```shell
git tag -l "hello*"
```
* 특정 문자가 들어있는 태그들을 리스트로 보여준다.
