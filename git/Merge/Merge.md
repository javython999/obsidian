>fast-forward merges
![[Pasted image 20231219214822.png]]
![[Pasted image 20231219214748.png]]
* master 브랜치에 변화가 없고 feature A 브랜치의 기능이 완성되어 merge가 필요할 경우 master 브랜치의 포인터를 이동시킨다.
* 간단하고 빠르지만 merge 기록이 안남는다.
```shell
git checkout master
git merge feature-a
```

>three-way merges (master branch에 변동이 없는 경우)
![[Pasted image 20231219214822.png]]
![[Pasted image 20231219215017.png]]
* 별도의 mergre commit을 만들어서 merge한다.
```shell
# master branch에 변화가 없는 경우
git checkout master
git merge --no-ff feature-a
git branch -d feature-a
```

>three-way merges (master branch에 변동이 있는 경우)
![[Pasted image 20231219221550.png]]
![[Pasted image 20231219221535.png]]
* feature-a branch가 파생된 이후 master branch에서 g 커밋이 생성된경우 fast-forward merges가 불가능하게 된다.(하게 되면 g커밋 변경사항을 잃어버리게 된다.)
```shell
git checkout master
git merge feature-a #  fast-forward merges가 불가능하므로 자동으로 three-way merge
```