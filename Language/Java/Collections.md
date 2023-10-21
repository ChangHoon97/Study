### Collections Framework
- 데이터 군을 저장하는 클래스들을 표준화한 설계
- List, Set, Map

<br>

### List
- 순서가 있는 데이터의 집합
- 데이터의 중복 허용
- Collection 인터페이스를 상속
- 구현 클래스 : ArrayList, LinkedList, Stack, Vector

<br>

### Set
- 순서가 없는 데이터의 집합
- 데이터의 중복 불가
- Collection 인터페이스를 상속
- 구현 클래스 : HahsSet, TreeSet


<br>

### Map
- Key와 Value의 쌍으로 이루어진 데이터 집합
- 순서가 유지되지 않는 데이터 집합
- Key 데이터는 중복 허용
- Value 데이터는 중복 불가
- 구현 클래스 : HashMap, TreeMap, HashTable, Properties
- #### MultiValueMap
  - Map의 형태를 하고 있지만 데이터의 중복이 가능한 형태

<br>

### Iterator
- 컬렉션에 저장된 요소들을 읽어오는 방법을 표준화한 것
- 단방향으로만 읽기 가능(양방향 읽기는 ListIterator 사용)
- Iterator<String> testIterator = testList.iterator();
- 메서드 : boolean hasNext(), Object next(), void remove();


<br>

### Collection 인터페이스 메서드
- boolean add(Object o) : 지정된 객체(o)를 Collection에 추가한다.
- void remove(Object o) : 지정된 객체(o)를 삭제한다.
- void clear() : Collection의 모든 객체를 삭제한다.
- Iterator iterator() : Collection의 Iterator를 반환
- boolean contains(Object o) : 지정된 객체(o)가 Collection에 포함되어있는지 확인한다.
- boolean isEmpty() : Collection이 비어있는지 확인한다.
- **boolean removeAll(Collection c)** : Collection(c)에 포함된 객체들을 삭제한다
- **boolean retainAll(Collection c)** :  Collection(c)에 포함된 객체만 남기고 나머지를 삭제한다. (Collection에 변화가 있다면 true 반환)
- int size() : Collection에 저장된 객체의 개수를 반환

<br>
<br>

### List 인터페이스 메서드
- void add(int index, Object element) : 지정된 index에 객체 삽입(중간에 삽입 될 경우 뒤에 객체들의 index가 한개씩 밀린다)
- Object get(int index) : index에 있는 객체 반환
- int indexOf(Object o) / int lastindexOf(Object o) : 지정된 객체의 index를 반환

<br>
<br>


### Map 인터페이스 메서드
- void clear() : Map의 모든 객체 삭제
- boolean containsKey(Object key) : 지정된 key와 일치하는 key가 있는지 확인
- boolean containsValue(Object value) : 지정된 value와 일치하는 value가 있는지 확인
- Object get(Object key) : 지정한 key에 대응하는 value를 반환
- boolean isEmpty() : Map이 비어있는지 확인
- Set keySet() : Map에 저장된 모든 key를 반환
- Object put(Object key, Object value) : Map에 key와 value를 저장
- int size() : Map에 저장된 key-value 쌍의 개수를 반환
- Collection values() : Map에 저장된 모든 value를 반환
