# Ch4.생성자

# 생성자

## 사용하는 이유

- 객체를 생성하고 나면 name, age, grade 같은 변수에 초기값을 설정한다.
- 생성 → 초기값 설정 필수적
- 그런데 이렇게 객체를 생성할때마다 초기값을 직접 설정하면 코드가 반복된다.

→ 그래서 ! 생성자가 필요

# this

- 멤버 변수와 메서드의 매개변수의 이름이 같을 때  매개변수가 코드 블럭의 더 안쪽에 있어서 매개변수가 우선순위를 가진다.
- 이때 멤버변수에 접근하려면 앞에 this. 해주면 ok!
- 여기서 this는 인스턴스 자신을 가리킴

![image](https://github.com/user-attachments/assets/6ce26187-78a8-41a7-b059-3bf1b2207604)

- 하지만 this 생략 가능
    - 변수를 찾을 때 가까운 지역변수(매개변수도 지역변수다)를 먼저 찾고 없으면 그 다음으로 멤버 변수를 찾는다. 멤버 변수도 없으면 오류가 발생

# 생성자

- 프로그래밍을 할때 객체를 생성하고 이후에 바로 초기값 할당해야하는데
- 직접 할 필요 없이 생성자 메서드를 사용!!
    - 생성자의 이름은 클래스 이름과 같아야 한다. 따라서 첫 글자도 대문자로 시작한다.
    - 생성자는 반환 타입이 없다. 비워두어야 한다.
    - 나머지는 메서드와 같다.
- 생성자 덕분에 객체를 생성하면서 동시에 생성 직후에 필요한 작업을 한번에 처리

```java
//생성자 등장 전
MemberInit member = new MemberInit();
member.initMember("user1", 15, 90);
//생성자 등장 후
MemberConstruct member = new MemberConstruct("user1", 15, 90);
```

## 기본 생성자

- 매개변수가 없는 생성자를 기본 생성자라 한다.
- 클래스에 생성자가 하나도 없으면 자바 컴파일러는 매개변수가 없고, 작동하는 코드가 없는 기본 생성자를 자동으로 만들어준다.
- 생성자가 하나라도 있으면 자바는 기본 생성자를 만들지 않는다.

---

### 정리

- 생성자는 반드시 호출되어야 한다.
- 생성자가 없으면 기본 생성자가 제공된다.
- 생성자가 하나라도 있으면 기본 생성자가 제공되지 않는다. 이 경우 개발자가 정의한 생성자를 직접 호출해야 한다.

## 생성자 - 오버로딩과 this()

```java
package javastudy_0807;

public class Book {
    String title;
    String author;
    int page;

    Book(){
        this("","",0);
    }
    Book(String title, String author){
        this(title, author,0);
    }
    Book(String title, String author,int page){
        this.title= title;
        this.author = author;
        this.page = page;
    }

    public void displayInfo(){
        System.out.println("제목: " + this.title+", 저자: "+ this.author + ", 페이지: " + this.page );
    }
}
```

- this() 를 사용하면 생성자 내부에서 다른 생성자를 호출
- 생성자를 오버로딩 한 덕분에 페이지 입력이 꼭 필요한 경우에는 page가 있는 생성자를 호출하면 되고, 그렇지 않은 경우에는 page가 없는 생성자를 호출하면 된다.
- page가 없는 생성자를 호출하면 페이지는 0!!
