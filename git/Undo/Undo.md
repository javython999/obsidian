>git restore 파일명
```shell
git restore a.txt
git restore --staged a.txt # working으로 옮긴다.
```
* 파일이 working에 있을 경우 변경사항을 초기화 한다.
* 파일이 staging에 있을 경우 working으로 옮긴다.

>git  reset HEAD .
```shell
git reset HEAD .
```
* 특정 포인터로 맞게 초기화
