# Ch5.패키지

# 패키지

- 패키지를 사용하는 경우 항상 코드 첫줄에 package pack 과 같이 패키지 이름을 적기
- 다른 패키지에서 이 클래스의 생성자를 호출하려면 public 을 사용해야 한다
- 사용자와 다른 위치: PackageMain1 과 User 는 서로 다른 패키지다. 이렇게 패키지가 다르면 pack.a.User 와 같이 패키지 전체 경로를 포함해서 클래스를 적어주어야 한다.

## 패키지 - import

- 패키지가 다를때 항상 pack.a.User와 같이 전체 경로를 적어주는 것은 불편 → import 사용!
- 코드에서 첫줄에는 package 를 사용하고, 다음 줄에는 import 를 사용
- import 를 사용하면 다른 패키지에 있는 클래스를 가져와서 사용할 수 있다.
- import 를 사용한 덕분에 코드에서는 패키지 명을 생략하고 클래스 이름만 적을 수 있다

```java
package pack;
import pack.a.*; //pack.a의 모든 클래스 사용

public class PackageMain2 {
 public static void main(String[] args) {
	 Data data = new Data();
	 User user = new User(); //import 사용으로 패키지 명 생략 가능
 }
}
```

**클래스 이름 중복일때**

```java
package pack;

import pack.a.User;

public class PackageMain3 {

 public static void main(String[] args) {
	 User userA = new User();
	 pack.b.User userB = new pack.b.User();
 }
}
```

- 같은 이름의 클래스가 있다면 import는 둘 중 하나만 선택
- 자주 쓰는 클래스를 import 하고 나머지를 패키지를 포함한 전체 경로 적어주면 된다.

# 패키지 규칙

- 패키지의 이름과 위치는 폴더(디렉토리) 위치와 같아야 한다. (필수)
- 패키지 이름은 모두 소문자를 사용한다. (관례)
- 패키지 이름의 앞 부분에는 일반적으로 회사의 도메인 이름을 거꾸로 사용한다. 예를 들어,
com.company.myapp 과 같이 사용한다. (관례)
    - 이 부분은 필수는 아니다. 하지만 수 많은 외부 라이브러리가 함께 사용되면 같은 패키지에 같은 클래스 이름이 존재할 수도 있다. 이렇게 도메인 이름을 거꾸로 사용하면 이런 문제를 방지할 수 있다.
