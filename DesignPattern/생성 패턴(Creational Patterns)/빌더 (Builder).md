복잡한 객체의 생성과정과 표현방법을 분리하여 다양한 구성의 인스턴스를 만드는 생성 패턴이다.
<span style="background:#9254de"><font color="#ffffff">생성자에 들어갈 매개 변수를 메서드로 하나하나 받아들이고 마지막에 통합 빌드</font></span>해서 객체를 생성하는 방식이다.
<br><br>
```java
// 생성자를 사용하는 경우(점층적 생성자 패턴)
Hamburger cheezburger = new Hamburger("참깨빵", "beef", 1, 1, 2);
Hamburger shrimpburger = new Hamburger("참깨빵", "shrimp", 1, null, 2);
```
생성자를 사용하는 경우에 매개 변수의 개수가 많아지면 매개 변수의 순서에 따라 어떤 값을 넣어야 하는지 헷갈릴 수 있다. 경우에 따라 ``null``을 매개 변수로 넣어주어야 하는 경우도 발생한다.
또 인스턴스에 따라 생성시 필요한 매개 변수가 다르다면 그 만큼 생성자 오버로딩 해야한다.
<br><br>
```java
// setter를 사용하는 경우(자바 bean 패턴)
Hamburger cheezburger = new Hamburger();
cheezburger.setBun("참깨빵");
cheezburger.setPatty("beef");
cheezburger.setOnion(1);
cheezburger.setTomato(1);
cheezburger.setCheez(2);

Hamburger shrimpburger = new Hamburger();
cheezburger.setBun("참깨빵");
cheezburger.setPatty("shrimp");
cheezburger.setOnion(1);
cheezburger.setTomato(1);
```
생성자를 사용 할 때보다는 가독성이 좋아지고 필요한 setter만 호출하기 때문에 유연하게 인스턴스를 생성할 수 있다. 하지만 생성 시점에 필요한 값들을 주입하는게 아니라 생성 후 값을 주입하기 때문에 일관성과 불변성의 문제가 나타난다.

* 일관성
 개발자가 실수로 ``setBun()``을 호출하지 않는다면 모든 ``Hamburger``객체에 꼭 있어야 하는 ``bun``필드의 값이 없게 된다.  
* 불변성
 ``setter``메서드는 객체를 처음 생성할 때 필드에 값을 할당하기 위해 존재하는 메서드다. 하지만 객체 생성 후에도 ``setter``메서드를 호출 할 수 있기 때문에 객체의 값이 변할 수가 있다.
<br><br>
빌더 패턴을 사용하기 위해 객체와 빌더를 생성해주어야 한다.
* 객체
```java
public class Hamburger {
	private String bun;
	private String patty;
	private int onion;
	private int tomato;
	private int cheez;

	public Hamburger(String bun, String patty, int onion, int tomato, int cheez) {
		this.bun = bun;
		this.patty = patty;
		this.onion = onion;
		this.tomato = tomato;
		this.cheez = cheez;
	}
}
```
<br><br>
* 빌더
```java
public class HamburgerBuilder {
	private String bun;
	private String patty;
	private int onion;
	private int tomato;
	private int cheez;
	
	public HamburgerBuilder bun(String bun) {
		this.bun = bun;
	}
	
	public HamburgerBuilder patty(String patty) {
		this.patty = patty;
	}
	
	public HamburgerBuilder onion(int onion) {
		this.onion = onion;
	}
	
	public HamburgerBuilder tomato(int tomato) {
		this.tomato = tomato;
	}
	
	public HamburgerBuilder cheez(int cheez) {
		this.cheez = cheez;
	}
	
	public Hamburger build() {
		return new Hamburger(bun, patty, onion, tomato, cheez);
	}
	
}
```
<br><br>
Builder 사용

````java
public static void main(String[] args) { 
	Hamburger cheezburger = new HamburgerBuilder()
									.bun("참깨빵")
									.patty("beef")
									.onion(1)
									.tomato(1)
									.cheez(1)
									.build();
}
````

* 장점
	* 가독성
		생성자 방식의 경우 매개 변수의 수가 증가할 수록 가독성이 급격히 떨어지지만 빌더 패턴은 <span style="background:#9254de"><font color="#ffffff">직관적으로 파악</font></span>할 수 있다.
	* 필수 멤버 변수와 선택적 멤버 변수를 분리
		생성자 방식의 경우 선택적 멤버 변수가 필요 없을 경우 ``null``을 매개 변수로 넘겨 생성을 한다. 빌더 패턴에서는 필수인 멤버 변수를 빌더의 생성자에 매개 변수로 지정해놓고 선택변수는 메서드로 정의하면 필수와 선택을 분리할 수 있다.
		```java
		Hamburger cheezburger = new HamburgerBuilder("참깨빵", "beef") // 필수
									.onion(1)  // 선택
									.tomato(1) // 선택
									.cheez(1)  // 선택
									.build();
		```
* 단점
	* 코드 복잡성 증가
		N개의 클래스에 대한 N개의 빌더 클래스가 필요하게 되므로 클래스가 증가 할 수록 코드가 많이 늘어나게 된다.
	* 생성자 보다는 성능 저하
		매번 메서드를 호출하여 빌더를 거쳐 인스턴스화 하기 때문에 성능이 떨어진다.
<br><br>

## 심플 빌더 패턴(Effective Java)
보통 개발자들이 빌더 패턴을 말할 때 정의되는 것이 이펙티브 자바에서 소개한 빌더 패턴이다.
GoF 빌더 패턴과 구별하기 위해 심플 빌더 패턴(Simple Builder Pattern)이라고도 불리운다.

심플 빌더 패턴은 생성자가 많은 경우 또는 변경 불가능한 불변 객체가 필요한 경우 코드의 가독성과 일관성, 불변성을 유지하는 것에 중점을 둔다. 심플 빌더 패턴은 앞서 설명한 빌더 패턴과 거의 차이가 없다. 다만 빌더 클래스가 구현 할 클래스의 정적 내부 클래스(Static Inner Class)로 구현된다는 점이 다르다.

```java
public class Hamburger {
	private String bun;
	private String patty;
	private int onion;
	private int tomato;
	private int cheez;
	
	// private 생성자
	private Hamburger(HamburgerBuilder builder) {
		this.bun = builder.bun;
		this.patty = builder.patty;
		this.onion = builder.onion;
		this.tomato = builder.tomato;
		this.cheez = builder.cheez;
	}
	
	// 정적 내부 빌더 클래스
	public static class HamburgerBuilder {
		private String bun;
		private String patty;
		private int onion;
		private int tomato;
		private int cheez;
		
		public HamburgerBuilder bun(String bun) {
			this.bun = bun;
			return this;
		}
		public HamburgerBuilder patty(String patty) {
			this.patty = patty;
			return this;
		}
		public HamburgerBuilder onion(int onion) {
			this.onion = onion;
			return this;
		}
		public HamburgerBuilder tomato(int tomato) {
			this.tomato = tomato;
			return this;
		}
		public HamburgerBuilder cheez(int cheez) {
			this.cheez = cheez;
			return this;
		}
		public Hamburger build() {
			return new Hamburger(this);
		}
	}
}

```

사용 예시
```java
Hamburger cheezburger = new Hamburger
							.HamburgerBuilder()
							.bun("참깨빵")
							.patty("beef")
							.onion(1)
							.tomato(1)
							.cheez(1)
							.build();
```

빌더 클래스를 static inner class로 구현하는 이유는 다음과 같다.
* 하나의 빌더 클래스는 하나의 대상 객체 생성만을 위해 사용된다. 그래서 두 클래스를 물리적으로 그룹핑함으로써 두 클래스간 관계 파악이 쉽다.
* 대상 객체는 오로지 빌더 객체에 의해 초기화 된다. 즉, 생성자를 외부에 노출시키면 안되기 때문에 생성자를 private으로 하고, 내부 빌더 클래스에서 private 생성자를 호출 함으로써 오로지 빌더객체에 의해 초기화 하도록 설계할 수 있다.
* static인 이유는 정적 내부 클래스는 외부 클래스의 인스턴스 없이도 생성할 수 있기 떄문이다.
<br><br>
## 디렉터 빌더 패턴(GoF)![[directorBuilderPatternDiagram.svg]]

GoF에서 정의하고 있는 디자인 패턴은 복잡한 객체의 생성 알고리즘과 조립 방법을 분리하여 빌드 공정을 구축하는 것이 목적이다. 빌더를 받아 조립 방법을 정의한 클래스를 '디렉터'라고 부른다.
심플 빌더 패턴은  하나의 대상 객체에 대한 생성만을 목적으로 하나, 디렉터 빌더 패턴은 여러가지의 빌드 형식을 유연하게 처리하는 것을 목적으로 한다. 일반적인 빌더 패턴을 고도화한 빌더 패턴이라고 할 수 있다.

* 대상 객체
```java
public class Hamburger {
	private String bun;
	private String patty;
	private int onion;
	private int tomato;
	private int cheez;
	
	//Setter
}
```
<br>

* 빌더(추상 클래스)
```java
public abstrct class HamburgerBuilder {
	protected Hamburger hamburger;
	
	public Hamburger getHamburger() {
		return this.hamburger;
	}

	public void createHamburger() {
		hamburger = new Hamburger();
	}
	
	public abstract bun();
	public abstract patty();
	public abstract onion();
	public abstract tomato();
	public abstract cheez();
	
}
```
<br>

* 콘크리트 빌더
```java
public class CheezBurgerBuilder extends HamburgerBuilder {
	@Override
	public bun() {
		hamburger.setBun("참깨빵");
	}
	
	@Override
	public patty() {
		hamburger.patty("beef");
	}
	
	@Override
	public onion() {
		hamburger.onion(1);
	}
	
	@Override
	public tomato() {
		hamburger.tomato(1);
	}
	
	@Override
	public cheez() {
		hamburger.cheez(2);
	}
}
```

```java
public class ShrimpBurgerBuilder extends HamburgerBuilder {
	@Override
	public bun() {
		hamburger.setBun("참깨빵");
	}
	
	@Override
	public patty() {
		hamburger.patty("shirimp");
	}
	
	@Override
	public onion() {
		hamburger.onion(1);
	}
	
	@Override
	public tomato() {
		hamburger.tomato(1);
	}
	
	@Override
	public cheez() {
		hamburger.cheez(null);
	}
}
```

* 디렉터
```java
public class BurgerKing {
	private HamburgerBuilder builder;
	
	public void setBuilder(HamburgerBuilder builder) {
		this.builder = builder;
	}
	
	public Hamburger getHamburger() {
		return this.builder.getHamburger();
	}
	
	public void constructHamburger() {
		this.builder.createHamburger();
		this.builder.bun();
		this.builder.patty();
		this.builder.onion();
		this.builder.tomato();
		this.builder.cheez();
	}
}
```

* 클라이언트
```java
public class Client {
    public static void main(String[] args) {
        // Director 생성
        BurgerKing burgerKing = new BurgerKing();
        
        //Concrete Builder 생성
        CheezBurgerBuilder cheezBurgerBuilder = new CheezBurgerBuilder();
        ShrimpBurgerBuilder shrimpBurgerBuilder = new ShrimpBurgerBuilder();
        
        burgerKing.setBuilder(cheezBurger);
        burgerKing.constructHamburger();
        Hamburger cheezBurger = burgerKing.getHamburger(); // product 획득
        
        burgerKing.setBuilder(shrimpBurgerBuilder);
        burgerKing.constructHamburger();
        Hamburger shrimpBurger = burgerKing.getHamburger(); // product 획득
    }
}
```
