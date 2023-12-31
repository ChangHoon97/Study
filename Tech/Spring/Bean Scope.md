## 빈 스코프
- 빈이 존재할 수 있는 범위

### 싱글톤 : 기본 스코프, 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프이다.
- 항상 같은 인스턴스의 스프링 빈을 반환한다. (객체를 한개만 생성하는 것)


### 프로토타입 : 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 매우 짧은 범위의 스코프이다.
- 항상 새로운 인스턴스를 생성해서 반환한다.
- 프로토타입 빈을 생성하고 의존관계 주입, 초기화까지만 처리한다.
- 프로토타입 빈을 관리할 책임은 프로토타입 빈을 받은 클라이언트에 있다.
- 종료 메서드에 대한 호출도 클라이언트가 직접 해야한다.


### 웹 관련 스코프
 - request : 웹 요청이 들어오고 나갈 때까지 유지되는 스코프
 - session : 웹 세션이 생성되고 종료될 때까지 유지되는 스코프
 - application : 웹의 서블릿 컨텍스와 같은 범위로 유지되는 스코프
