### Generics : 데이터 타입을 매개변수로 사용하는 프로그래밍 기법


## 예시
```java
class Container<T> {
    private T value;

    public Container(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }

    public void setValue(T value) {
        this.value = value;
    }
}
```
- T는 type varaible 이라고 하며 실제 사용할때는 실제 타입을 지정해줘야 한다.

```java
Container<String> stringContainer = new Container<>("Hello");
String stringValue = stringContainer.getValue(); // "Hello"

Container<Integer> intContainer = new Container<>(42);
int intValue = intContainer.getValue(); // 42
```
