### 열거형(enum)
- 서로 관련된 상수를 편리하게 선언하기 위한 것으로 여러 상수를 정의할 때 사용하면 유용하다.

```java
class Card{
    static final int CLOVER = 0;
    static final int HEART = 1;
    static final int DIAMOND = 2;
    static final int SPADE = 3;

    static final int TWO = 0;
    static final int THREE = 1;
    static final int FOUR = 2;
    
    final int kind;
    final int num;
}
```

위 예시 코드를 enum으로 변경하면

```java
class Card{
    enum Kind {CLOVER, HEART, DIAMOND, SPADE}
    enum Value {TWO, THREE, FOUR}

    final Kind kind;
    final Value value;
}
```

- JAVA의 열거형은 '타입에 안전한 열거형' 이라서 실제 값이 같아도 타입이 다르면 컴파일 에러가 발생한다.


## enum과 생성자, 메서드 예시

```java
public enum CoffeeSize {
    SMALL(8),
    MEDIUM(12),
    LARGE(16);

    private int ounces;

    CoffeeSize(int ounces) {
        this.ounces = ounces;
    }

    public int getOunces() {
        return ounces;
    }
}
```

위 enum을 활용하는 예시

```java
public class Main {
    public static void main(String[] args) {
        // 열거형 상수 사용
        CoffeeSize smallSize = CoffeeSize.SMALL;
        CoffeeSize mediumSize = CoffeeSize.MEDIUM;
        CoffeeSize largeSize = CoffeeSize.LARGE;

        // 열거형 상수의 값 출력
        System.out.println("Small size: " + smallSize.getOunces() + " ounces");
        System.out.println("Medium size: " + mediumSize.getOunces() + " ounces");
        System.out.println("Large size: " + largeSize.getOunces() + " ounces");

        // 열거형을 배열로 만들기
        CoffeeSize[] allSizes = CoffeeSize.values();
        System.out.println("All Sizes:");
        for (CoffeeSize size : allSizes) {
            System.out.println(size + " - " + size.getOunces() + " ounces");
        }
    }
}
```