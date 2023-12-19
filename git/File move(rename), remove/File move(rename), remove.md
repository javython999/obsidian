>git rm 

```shell
rm a.txt # 파일 삭제 -> working의 a.txt 삭제내역을 staging으로 옮겨야 됨
git rm a.txt # 파일 삭제 & a.txt 삭제내역을 바로 staging함
```

>git move
```shell
mv a.txt b.txt # a.txt를 b.txt로 이름변경 -> 파일명 변경 내역을 staging으로 옮겨야 됨
git mv a.txt b.txt # 파일명 변경 & 파일명 변경내역을 바로 staging
```
