# 추상 메서드와 추상 클래스

### 추상 메소드
- 추상 메소드는 자식 클래스에서 반드시 오버라이딩해야만 사용할 수 있는 메소드를 의미합니다.
- 자바에서 추상 메소드를 선언하여 사용하는 목적은 추상 메소드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메소드를 구현하도록 하기 위함입니다.
- 추상 메소드는 선언부만 존재하며, 구현부는 작성되어 있지 않습니다. (작성되어 있지 않은 구현부를 자식 클래스에서 오버라이딩하여 사용하는 것입니다.)

```java
abstract 반환타입 메소드이름();
```
구현부는 없다는 의미로 선언부 끝에 바로 세미콜론을 추가합니다.


<br>

### 추상 클래스
- 자바에서는 하나 이상의 추상 메소드를 포함하는 클래스를 카리켜 추상 클래스라고 합니다.
- 이러한 추상 클래스는 객체 지향 프로그래밍에서 중요한 특징인 `다형성`을 가지는 메소드의 집합을 정의할 수 있도록 합니다.
- 즉, 반드시 사용되어야 하는 메소드를 추상 클래스에 추상 메소드를 선언해 놓으면 , 이 클래스를 상속받는 모든 클래스에서는 이 추상 메소드를 반드시 재정의 해야합니다.

```java
abstract class ClassName{
  // ...
  abstract 반환타입 메소드이름();
}
```
이러한 추상 클래스는 동작이 정의되어 있지 않은 추상 메소드를 포함하고 있으므로, `인스턴스 생성이 불가능`합니다.  
추상 클래스는 먼저 상속을 통해 자식 클래스를 만들고, 만든 자식 클래스에서 추상 클래스의 모든 추상 메소드를 오버라이딩하고 나서야 비로소 자식 클래스의 인스턴스를 생성할 수 있게 됩니다.

> 추상 클래스는 추상 메소드를 포함하고 있다는 점을 제외하면, 일반 클래스와 모든 점이 같습니다. 
> 즉 , 생성자와 필드, 일반 메소드도 포함할 수 있습니다.

```java
abstract class Animal {
  abstract void cry();
}
class Cat extends Animal{
  void cry() {
    System.out.println("야옹");
  }
}
public class PolymorphismEx02{
  // Animal a = new Animal(); 추상 클래스는 인스턴스 생성 불가능
  Cat c = new Cat();
  
  c.cry(); // 야옹
}
```

<br>

### 추상 메서드의 사용 목적
- 추상 메서드가 포함된 클래스를 상속받는 자식 클래스가 반드시 추상 메서드를 구현하도록 하기 위함.
- 만약 일반 메소드로 구현한다면 사용자에 따라 해당 메소드를 구현할 수도 있고, 안 할 수도 있습니다.