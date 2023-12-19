>merge 실행시 충돌이 날 경우 Auto-merging이 실패하고 안내 메세지가 나온다.
![[Pasted image 20231219223033.png]]

>git status로 충돌 파일을 확인
![[Pasted image 20231219223140.png]]

> 양쪽에서 수정(충돌)된 부분을 표시해준다.
![[Pasted image 20231219223156.png]]

>해당 파일을 열어 수동으로 처리를 한다. 그 후 해당 파일을 git add후 git merge --continue 명령어를 통해 merge를 마무리 한다.
```shell
git merge --continue

git merge --abort # merge 중단
git clean -fd # 현재 디렉토리를 클린(orgi 파일 삭제)
```


>VS Code로 Conflict 해결하기
```shell
git config --global -e
```

> 아래 옵션을 추가
```groovy
[merge]
  tool = vscode
[mergetool "vscode"]
  cmd = code --wait $MERGED
```

>git merge feature 실행후 conf
![[Pasted image 20231219224409.png]]
```shell
git mergetool # 지정한 vscode 실행
```

>vscode에서 수정후 파일 저장
![[Pasted image 20231219224502.png]]
>.orig 파일
![[Pasted image 20231219224644.png]]
* conflict 내용이 저장된다. (orig 파일 생성은 옵션으로 끌 수 있다.)

```shell
$ git config --global mergetool.keepBackup false
```

> git add후 git merge --continue 명령어를 통해 merge를 마무리 한다.
```shell
git merge --continue
```
