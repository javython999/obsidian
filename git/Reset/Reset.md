>git reset --soft
```shell
git reset --soft 해시코드 또는 HEAD포인터
```
* 해당 해시코드 또는 HEAD포인터가 가르키는 커밋상태로 되돌린다.
* 해당 버전에서 작업했던 파일들은 staging 상태로 체크아웃된다.

>git reset --hard 
```shell
git reset --hard 해시코드 또는 HEAD포인터
```
* 해당 해시코드 또는 HEAD포인터가 가르키는 커밋 상태로 되돌린다.
* 해당 버전에서 작업했던 파일들은 존재하지 않는다.