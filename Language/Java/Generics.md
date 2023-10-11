### Generics : 데이터 타입을 매개변수로 사용하는 프로그래밍 기법

// Generics를 사용한 클래스
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


Container<String> stringContainer = new Container<>("Hello");
String stringValue = stringContainer.getValue(); // "Hello"

Container<Integer> intContainer = new Container<>(42);
int intValue = intContainer.getValue(); // 42
