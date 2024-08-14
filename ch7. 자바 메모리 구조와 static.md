# 자바 메모리 구조와 static


![image](https://github.com/user-attachments/assets/69d10c9b-fb08-4858-a6ff-3544ad7d07bb)
![image](https://github.com/user-attachments/assets/f83053c8-30ba-4e33-b553-b3ae7c8faf96)

- 자바의 메모리 구조 : 메서드 영역, 스택 영역, 힙 영역
    - 메서드 영역: 클래스 정보 보관, 프로그램을 실행하는데 필요한 공통 데이터 관리
        - 클래스 정보
        - static 영역 : static변수 보관
        - 런타임 상수 풀: 프로그램을 실행하는데 필요한 공통 리터럴 상수 보관
          <br/><br/>
    - 스택 영역: 실제 프로그램이 실행되는 영역, 메서드를 실행 할 때, 하나씩 쌓임
        - 스택 프레임: 스택 영역에 쌓이는 네모 박스가 하나의 스택 프레임
          <br/><br/>
    - 힙 영역: 객체(인스턴스)가 생성되는 영역, 배열도 이 영역에 생성됨, 가비지 컬렉션(GC)이 이루어지는 주요 영역
<br/><br/>
# 스택과 큐 자료 구조

## 스택 구조

![image](https://github.com/user-attachments/assets/f7d4db4e-d818-48cf-b4c6-1521be99d1f5)

- 후입선출(LIFO, Last In First Out)
- 선입선출(FIFO, First In First Out)


## 큐 자료 구조
![image](https://github.com/user-attachments/assets/34c77ecc-f525-4fc0-92bc-791cedd00919)

# 스택 영역

- 자바는 스택 영역을 사용해서 메서드 호출과 지역 변수를 관리
- 메서드 호출 시 스택 프레임 쌓임
- 스택 프레임 종료시 지역 변수도 함께 제거
- 스택 프레임이 모두 제거 되면 프로그램 종료

## 스택 영역과 힙 영역

![image](https://github.com/user-attachments/assets/d10ec863-099f-4a81-af97-ac338cc43251)


- 객체 참조 시
  <br/><br/>

![image](https://github.com/user-attachments/assets/52a8b103-17b3-48cc-8776-b09ae1ca8912)


- gc 대상
<br/><br/>
# static 변수

- static 사용 안하고 객체를 매번 만들면 이렇게 새로운 변수로 계속 생성됨

![image](https://github.com/user-attachments/assets/e5c4751e-b29d-4983-867b-65c8bf7f82df)


→ 이거 해결을 위해 static 쓰면 됨 → 그리고 이때 쓰이는게 힙영역이 아닌 메서드 영역

<br/><br/>
- static 사용시

![image](https://github.com/user-attachments/assets/a752aaa3-5e7b-4962-a4be-f2c6633ea790)

- static 이 붙은 멤버 변수는 메서드 영역에서 관리
    - static 이 붙은 멤버 변수 count 는 인스턴스 영역에 생성되지 않는다. 대신에 메서드 영역에서 이 변수를 관리
    

<aside>
💡 static 변수는 쉽게 이야기해서 클래스인 붕어빵 틀이 특별히 관리하는 변수이다. 붕어빵 틀은 1개이므로 클래스 변
수도 하나만 존재한다. 반면에 인스턴스 변수는 붕어빵인 인스턴스의 수 만큼 존재

</aside>

<br/><br/>
**멤버 변수(필드)의 종류**

- 인스턴스 변수: static 이 붙지 않은 멤버 변수, 예) name
    - static 이 붙지 않은 멤버 변수는 인스턴스를 생성해야 사용할 수 있고, 인스턴스에 소속
    - 인스턴스 변수는 인스턴스를 만들 때 마다 새로 만들어진다.
<br/><br/>
- 클래스 변수: static 이 붙은 멤버 변수, 예) count
    - 클래스 변수, 정적 변수, static 변수
    - static 이 붙은 멤버 변수는 인스턴스와 무관하게 클래스에 바로 접근해서 사용할 수 있고, 클래스 자체에
    소속
    - 클래스 변수는 자바 프로그램을 시작할 때 딱 1개가 만들어진다. 인스턴스와는 다르게 보통 여러곳에서 공유하는 목적
<br/><br/>
# static 메서드

정적 메서드는 정적 변수처럼 인스턴스 생성 없이 클래스 명을 통해서 바로 호출할 수 있다.

```java
public class DecoMain2 {
	 public static void main(String[] args) {
		 String s = "hello java";
		 String deco = DecoUtil2.deco(s); //이렇게 객체 생성 없이 바로 호출 가능
		 System.out.println("before: " + s);
		 System.out.println("after: " + deco);
	 }
}
```
<br/><br/>
## 정적 메서드 사용법
- static 메서드는 static만 사용할 수 있다.
- 반대로 모든 곳에서 static을 호출 할 수 있다.
    - 정적 메서드는 공용기능. 따라서 접근 제어자만 허락한다면 모든 곳에서 static 호출 가능
<br/><br/>
### 정적 메서드가 인스턴스의 기능을 사용할 수 없는 이유
정적 메서드는 클래스의 이름을 통해 바로 호출할 수 있다. 그래서 인스턴스처럼 참조값의 개념이 없다.
특정 인스턴스의 기능을 사용하려면 참조값을 알아야 하는데, 정적 메서드는 참조값 없이 호출한다. 따라서 정적 메서드 내부에서 인스턴스 변수나 인스턴스 메서드를 사용할 수 없다.
<br/><br/>
### main() 메서드는 정적 메서드!!
- 인스턴스 생성 없이 실행하는 가장 대표적인 메서드
- 정적 메서드는 정적 메서드만 호출
