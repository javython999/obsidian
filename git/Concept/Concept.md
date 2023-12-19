> git init

![[init.svg]]

>파일 생성

![[untracked.svg]]
* untracked 파일들은 git이 변경 사항을 추적하지 않는다.

>파일 tracked

![[tracked.svg]]
* tracked 파일은 git이 변경 사항을 추적한다.

> staging

![[staging.svg]]
* tracked 파일중 작업이 완료된 파일들은 staging으로 옮긴다. 
* tracked 파일중 변경사항이 있는 파일들만 staging으로 옮길 수 있다.
* staging에 있는 파일들만 commit 대상이 된다.

> commit

![[commit.svg]]
* 커밋 명령어를 통해 staging 파일을 git에 저장한다.

> checkout

![[checkout.svg]]
* checkout을 통해 깃에 저장된 파일을 언제든지 가져 올 수 있다.

> push

![[push.svg]]
* 깃에 저장된 파일을 원격저장소(git hub)에 저장한다.

> pull

![[pull.svg]]
* pull을 통해 원격 저장소에 있는 파일을 local로 가져온다.
