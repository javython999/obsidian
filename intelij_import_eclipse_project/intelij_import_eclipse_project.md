1. svn checkout
2. `Maven Project` 선택
   ![[Pasted image 20230924132635.png]]
3. Java version Setting
	1. `File` `fas:LongArrowAltRight` `Project Structure`
	   ![[Pasted image 20230924133556.png]]
	   ***
	2. `Project` `fas:LongArrowAltRight` `SDK` 설정
	   ![[Pasted image 20230924141933.png]]
4. Spring Setting
	1. `File` `fas:LongArrowAltRight` Project Structure (Ctr + Alt + Shift + S)
	   ![[Pasted image 20230924133556.png]]
	   ***
	2. `Modules` `fas:LongArrowAltRight`  `+`  클릭
	    ![[Pasted image 20230924130742.png]]
	    ***
	3. `Spring` 클릭
	   ![[Pasted image 20230924131144.png]]
	    ***
	4. `+` 클릭
	   ![[Pasted image 20230924142519.png]]
	   ***
	5.  `egov-com-servlet.xml` 체크
	   ![[Pasted image 20230924142635.png]]
	   ***
	6. `Apply` 클릭
	   ![[Pasted image 20230924143026.png]]
5. Maven 설정(Pom.xml)
   1. `<repository> ... </repository>` 설정
      인텔리제이의 기본 설정된 Maven버전에서는 `repository`의  url에 `http`사용을 금지하고 있다. `http`를 사용하는 url은 `https`로 변경한다.
      ```xml
      <url>http://maven.egovframe.go.kr/maven/</url>  변경 전
      <url>https://maven.egovframe.go.kr/maven/</url> 변경 후
      ```
      ***
   2. `<build> ... </build>` 설정
       인텔리제이는 `src/main/java`의 하위 패키지들에 들어있는 `xml`파일들을 빌드시 포함하지 않기 때문에 포함시키도록 설정한다.
       ```xml
       <resources>
	       <resource>
		       <directory>src/main/java</directory>  
	       </resource>
	       <resource>
		       <directory>src/main/resources</directory>  
	       </resource>
       </resources>
		```
    3. `Load Maven Changes`
      `pom.xml`에 설정한 사항들을 적용시킨다. `Load Maven Changes`을 눌러 적용할 수도 있고,
      `maven`메뉴에서 `Reload All maven Projects`를 눌러서 적용할 수도 있다.
	   ![[Pasted image 20230924150753.png]]
	   ![[Pasted image 20230924150654.png]]
6. Librarry 설정
	1. `File` `fas:LongArrowAltRight` Project Structure (Ctr + Alt + Shift + S)
	   ![[Pasted image 20230924133556.png]]
	   ***
	2. `Libraries` 클릭 `fas:LongArrowAltRight` `+` 클릭
	   ![[Pasted image 20230924143805.png]]
	   ***
	3. `Java` 클릭
	   ![[Pasted image 20230924144046.png]]
	   ***
	4. 프로젝트의 `lib` 선택 `fas:LongArrowAltRight` `OK` 클릭
	   ![[Pasted image 20230924144251.png]]
	   ***
	5. `Choose Moudles` `fas:LongArrowAltRight` `OK`
	   ![[Pasted image 20230924144439.png]]
	   ***
	6. `Apply` `fas:LongArrowAltRight` `OK`
	   ![[Pasted image 20230924144628.png]]
	   ***
	7. `Schedule for Addition` `fas:LongArrowAltRight` `Cancle`
	   ![[Pasted image 20230924144927.png]]
	   svn에서 관리하는 소스로 추가할 것인지 물어보는데 `.iml`파일은 인텔리제이 설정 파일이므로 svn에 공유할 필요가 없다. `Cancle`을 눌러준다.
