객체의 인스턴스를 오직 1개만 생성하는 패턴이다.
인스턴스가 필요할 때 똑같은 인스턴스를 새로 만들지 않고 기존의 인스턴스를 사용한다.
환경 설정 정보와 같은 객체는 여러개의 인스턴스가 있을 경우 문제가 발생할 수 있다.
즉 싱글톤은 다음 과 같은 상황에 사용을 한다.
- 프로그램 내에서 하나의 객체만 존재해야 한다.
- 프로그램 내에서 여러 부분에서 해당 객체를 공유하여 사용해야한다.
<br/><br/>
### 싱글톤 패턴의 장점
1. 메모리 측면의 이점
   한 개의 인스턴스를 고정 메모리 영역에 생성하고  공유하여 사용하기 때문에 메모리 낭비를 방지할 수 있다.
2. 속도 측면의 이점
   이미 생성된 인스턴스를 사용할 경우 인스턴스를 생성하는 과정이 필요 없기 때문에 속도 측면에 이점이 있다.
3. 데이터 공유가 쉽다
   한 개의 인스턴스를 전역으로 사용하기 때문에 여러 클래스에서 데이터를 공유하며 사용할 수 있다. 하지만 동시성 문제가 발생할 수 있기 때문에 이점에 유의해야 한다.
<br/><br/>
싱글톤 패턴 구현방법1
* 여러개의 인스턴스를 만들지 못하게 생성자를 `private`으로 선언.
* 생성자를 대신해 instance를 반환 해주는 `static` 메서드 선언.
* 싱글톤으로 인스턴스를 생성 할 수 있지만 멀티쓰레드 환경에서는 안전하지 않다.

```java
public class Settings {
	private static Settings instance;
	
	// 생성자를 private으로 하면 클래스 밖에서는 생성자로 인스턴스를 만들 수 없게 된다.
	private setting() {}
	
	public static Settings getInstance() {
		if(instance == null) {
			instance = new Setting();
		}
		return instance;
	}
}
```

<br/><br/>

싱글톤 패턴 구현방법2 (checked locking)
* 생성자를 대신하는 `static`메서드에 동기화(synchronized)를 사용해 멀티쓰레드 환경에 안전하게 만드는 방법
* getInstance()를 호출 할때마다 동기화 처리를 하는 작업 때문에 성능 저하가 발생 할 수 있다.
```java
public class Settings {
	private static Settings instance;
	
	private setting() {}
	
	public static synchronized Settings getInstance() {
		if(instance == null) {
			instance = new Setting();
		}
		return instance;
	}
}
```

<br/><br/>

싱글톤 패턴 구현방법3
이른 초기화 (eager initialization)을 사용하는 방법
* 인스턴스 생성시에 많은 자원이 소모되거나 시간이 걸리는 경우 미리 생성하는 점이 단점이 될 수 있다.
```java
public class Settings {
	private static Settings instance = new Settings();
	
	private setting() {}
	
	public static Settings getInstance() {
		return instance;
	}
}
```

<br/><br/>

싱글톤 패턴 구현방법4 (double checked locking)
* volatile 키워드 추가해야 한다.
* volatile 동작 원리는 복잡하다. 1.5이후 버전부터 사용가능하다.
```java
public class Settings {
	private static volatile Settings instance = new Settings();
	
	private setting() {}
	
	public static Settings getInstance() {
		if(instance == null) {
            synchronized(Settings.class) {
                if(instance == null) {
                    instance = new Settings();
                }
            }
        }
		return instance;
	}
}
```

