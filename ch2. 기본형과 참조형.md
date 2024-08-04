# 기본형 vs 참조형

|  | 기본형 | 참조형 |
| --- | --- | --- |
| 개념 | 변수에 사용할 값을 직접 넣을 수 있는 데이터 타입 | 데이터에 접근하기 위한 참조(주소)를 저장하는 데이터 타입 |
| ex | int, long, double, boolean | Student student1, int[] students 같은 객체 또는 배열 |
| 변수 대입 | 해당 값만 복사하여 대입 | 객체의 위치를 가리키는 참조값만 복사(실제 사용하는 객체X) |
| 메서드 호출 | 해당 값이 복사 → 메서드 내부에서 매개변수의 값을 변경해도, 호출자의 변수 값은 영향 X | 참조값이 복사 → 메서드 내부에서 매개변수로 전달된 객체의 멤버 변수를 변경하면, 호출자의 객체도 변경 |
- **대원칙: 자바는 항상 변수의 값을 복사해서 대입한다.**
- 기본형을 제외한 나머지는 모두 참조형
    - 기본형은 소문자로 시작
        - 기본형은 자바가 기본으로 제공하는 데이터 타입이다. 이러한 기본형은 개발자가 새로 정의할 수 없다
    - 클래스는 대문자로 시작
        - 클래스는 모두 참조형이다
- 참고 - String
    
    String 은 사실은 클래스다. 따라서 참조형
    
- 참조형의 값 복사
  
![image](https://github.com/user-attachments/assets/42692e61-a354-4719-b54b-88362f517648)


## 변수의 값 초기화

- 멤버 변수: 자동 초기화
    - 인스턴스의 멤버 변수는 인스턴스를 생성할 때 자동으로 초기화된다.
    - 숫자( int )= 0 , boolean = false , 참조형 = null ( null 값은 참조할 대상이 없다는 뜻으로 사용)
    - 개발자가 초기값을 직접 지정할 수 있다.
- 지역 변수: 수동 초기화

### null
![image](https://github.com/user-attachments/assets/73d29bac-2f5d-4db1-8563-65aa787e1cc0)


- Data 타입을 받을 수 있는 참조형 변수 data에 null 값을 할당
- 따라서 data 변수에는 아직 가리키는 객체가 없다는 뜻

### GC - 아무도 참조하지 않는 인스턴스의 최후

![image](https://github.com/user-attachments/assets/b4f855a8-c517-4c72-9270-fffcde274347)
![image](https://github.com/user-attachments/assets/45e6d732-f06a-4fb3-81e7-e40478f6fabe)

- data에 null을 할당하면 앞에서 생성한 x001 Data 인스턴스를 아무도 참조하지 않고 그러면 x001이라는 참조값을 다시 구할 방법이 없다.(= 해당 인스턴스에 다시 접근 불가능)
- 이렇게 아무도 참조하지 않는 인스턴스는 사용되지 않고 메모리 용량만 차지할 뿐
- (자바는) 아무도 참조하지 않는 인스턴스가 있으면 JVM의 GC(가비지 컬렉션)가 더
이상 사용하지 않는 인스턴스라 판단하고 해당 인스턴스를 자동으로 메모리에서 제거

## NullPointerException

- 참조값 없이 객체를 찾아가면 발생하는 문제
- NullPointerException 은 null 에 . (dot)을 찍었을 때 발생

```java
public class NullMain3 {
 public static void main(String[] args) {
 
 BigData bigData = new BigData();
 System.out.println("bigData.count=" + bigData.count);
 System.out.println("bigData.data=" + bigData.data);
 
 //NullPointerException
 System.out.println("bigData.data.value=" + bigData.data.value); 
 }
}
```


>💡 실행결과
>
>bigData.count=0bigData.data=null
>Exception in thread "main" java.lang.NullPointerException: Cannot read field
>"value" because "bigData.data" is null at ref.NullMain3.main(NullMain3.java:10)

- [bigData.data](http://bigData.data)를 출력하면 참조값인 null이 출력
- bigData.data.value 를 출력하면 data 의 값이 null 이므로 null 에 . (dot)을 찍게 되고 (null.value), 따라서 참조할 곳이 없으므로 NullPointerException 예외가 발생
