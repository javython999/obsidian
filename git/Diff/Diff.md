> git diff
```shell
git diff
```
* 아무런 옵션 없이 `git diff` 실행시 staging에 있는 파일의 변경사항을 보여준다.

>git difftool

git config에 다음과 같은 설정을 넣으면 vscode로 변경사항을 비교해볼 수 있다.
```groovy
[diff] 
	tool = vscode 
[difftool "vscode"] 
	cmd = code --wait --diff $LOCAL $REMOTE
```

```shell
git difftool
```