구체적으로 어떤 것을 만들지는 서브 클래스가 정한다. 즉 인스턴스 생성을 서브 클래스에 위임한다.
부모 추상 클래스는 인터페이스에만 의존하고 실제로 어떤 구현 클래스를 호출할지는 서브 클래스에서 구현한다.

![[ShipFactory Diagram.svg]]

```java
public interface ShipFactory {  
    default Ship orderShip(String name, String email) {  
        validate(name, email);  
  
        prepareFor(name);  
        Ship ship = createShip();  
  
        sendEmailTo(email, ship);  
        return ship;  
    }  
  
    Ship createShip();  
  
    private void validate(String name, String email) {  
        if (name == null || name.isBlank()) {  
            throw new IllegalArgumentException("배 이름을 지어주세요.");  
        }  
        if (email == null || email.isBlank()) {  
            throw new IllegalArgumentException("연락처를 남겨주세요.");  
        }  
    }  
  
    private void prepareFor(String name) {  
        System.out.println(name + " 만들 준비 중");  
    }  
  
    private void sendEmailTo(String email, Ship ship) {  
        System.out.println(ship.getName() + " 다 만들었습니다.");  
    }  
}
```

```java
public class WhiteShipFactory implements ShipFactory {  
  
    @Override  
    public Ship createShip() {  
        return new WhiteShip();  
    }  
}
```

```java
public class BlackShipFactory implements ShipFactory{  
    @Override  
    public Ship createShip() {  
        return new BlackShip();  
    }  
}
```


![[Ship Diagram.svg]]
```java
public class Ship {  
    private String name;  
  
    private String color;  
  
    private String logo;  
  
    public String getName() {  
        return name;  
    }  
  
    public void setName(String name) {  
        this.name = name;  
    }  
  
    public String getColor() {  
        return color;  
    }  
  
    public void setColor(String color) {  
        this.color = color;  
    }  
  
    public String getLogo() {  
        return logo;  
    }  
  
    public void setLogo(String logo) {  
        this.logo = logo;  
    }  
  
    @Override  
    public String toString() {  
        return "Ship{" +  
                "name='" + name + '\'' +  
                ", color='" + color + '\'' +  
                ", logo='" + logo + '\'' +  
                '}';  
    }  
}
```

```java
public class WhiteShip extends Ship{  
  
    public WhiteShip() {  
        setName("whiteShip");  
        setLogo("\uD83D\uDEE5");  
        setColor("white");  
    }  
}
```

```java
public class BlackShip extends Ship {  
  
    public BlackShip() {  
        setName("blackShip");  
        setLogo("⚓");  
        setColor("black");  
    }  
}
```

아래와 같이 활용한다.

```java
public class Client {  
  
    public static void main(String[] args) {  
        Client client = new Client();  
        client.print(new WhiteShipFactory(), "whiteShip", "test@naver.com");  
        client.print(new BlackShipFactory(), "blackShip", "test@naver.com");  
	 }  
    private void print(ShipFactory shipFactory, String name, String email) {  
        System.out.println(shipFactory.orderShip(name, email));  
    }  
  
}
```

확장이 필요한 경우 기존 코드 수정없이 ShipFactory을 구현하고 Ship을 상속한 클래스를 만들면 된다. 하지만 코드의 량이 늘어나는 단점이 있다.