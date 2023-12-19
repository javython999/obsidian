>모든 git 설정
```shell
git config --list
```

>에디터 열기
```shell
git config --global -e
```

>default 에디터 설정
```shell
git config --global core.editor "code --wait"
```
* "code --wait": 에디터가 열리게 되고 에디터를 닫을 때 까지 콘솔에 명령어 입력 불가.
* "code": 에디터가 열려도 콘솔에 명령어 입력 가능.

>사용자 설정
```shell
git config --global user.name "this_is_user_name" # 사용자 이름 설정
git config --global user.email "this_is_user_email" # 사용자 이메일 설정


# 설정 확인
git config user.name
# this_is_user_name

git config user.email
# this_is_user_email
```

>push & pull 설정
```shell
git config --global push.default "current" # 사용자 이름 설정
git config --global pull.rebase "true"
```
* push.default current: 로컬에 있는 브랜치 이름이 항상 remote와 동일하다고 설정해주어서 push 할때 마다 'git push --set-upstream origin master' 옵션을 작성하지 않아도 되게 해준다.
* pull.rebase true: pull 명령어는 mrege와 rebase 옵션을 선택할 수 있는데 기본으로 rebase로 설정해둔다.

>auto crlf 설정(줄바꿈 문자 설정)
   ![[Pasted image 20231217173058.png]]
   * 운영체제마다 에디터에서 줄바꿈 문자가 다르다.
   * 서로 다른 운영체제를 사용하는 사용자들끼리 코드 공유시 문제가 발생
   * 이걸 보정해주는 옵션이 autocrlf이다.
   * `windows`에서는 true, `mac`에서는 input으로 설정한다.
```shell
git config --global core.autocrlf true #for Windows 
git config --global core.autocrlf input #for Mac
```
