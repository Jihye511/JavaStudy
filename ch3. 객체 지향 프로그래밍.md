# 절차 지향 프로그래밍 VS 객체 지향 프로그래밍

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;절차 지향 프로그래밍&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 객체 지향 프로그래밍 |
| --- | --- |
| 실행 순서 중요 | 객체 중요 |
| 프로그램의 흐름을 순차적으로 따르며 처리| 실제 세계의 사물이나 사건을 객체로 보고 그 객체들 간의 상호작용을 중심으로 프로그래밍 |
| "어떻게”를 중심으로 | “무엇을”을 중심으로 |

<aside>
💡 절차 지향은 데이터와 해당 데이터에 대한 처리 방식이 분리되어 있다.

반면 객체 지향에서는 데이터와 그 데이터에 대한 행동(메서드)이 하나의 '객체' 안에 함께 포함되어 있다

</aside>

### 객체란?

- 속성(데이터)과 기능 딱 2가지
- 객체 지향 프로그래밍은 모든 사물을 속성과 기능을 가진 객체로 생각하는 것

# 절차 지향 프로그래밍의 한계

- 절차 지향 프로그래밍으로 작성한 코드의 한계는 바로 데이터와 기능이 분리되어 있다는 점이다.
- 데이터와 그 데이터를 사용하는 기능은 매우 밀접하게 연관되어 있다.
- 따라서 관련 데이터가 변경되면 그 부분의 메서드들도 함께 변경해야 한다.
- 이렇게 데이터와 기능이 분리되어 있으면 유지보수 관점에서도 관리 포인트가 2곳으로 늘어난다.

→ 그래서 객체지향 프로그래밍이 등장!! 

→ 얘는 데이터와 기능을 묶어서 프로그래밍

# 클래스와 메서드

- 클래스는 속성(데이터, 멤버 변수)과 기능(메서드)을 정의할 수 있다.
- 객체는 자신의 메서드를 통해 자신의 멤버 변수에 접근할 수 있다.
    - 객체의 메서드 내부에서 접근하는 멤버 변수는 객체 자신의 멤버 변수이다.

# 객체 지향 프로그래밍

예시

```java
package oop;
public class MusicPlayer {
 int volume = 0;
 boolean isOn = false;
 
 void on() {
	 isOn = true;
	 System.out.println("음악 플레이어를 시작합니다");
 }
 
 void off() {
	 isOn = false;
	 System.out.println("음악 플레이어를 종료합니다");
 }
 
 void volumeUp() {
	 volume++;
	 System.out.println("음악 플레이어 볼륨:" + volume);
 }
 
 void volumeDown() {
	 volume--;
	 System.out.println("음악 플레이어 볼륨:" + volume);
 }
 
 void showStatus() {
	 System.out.println("음악 플레이어 상태 확인");
	 if (isOn) {
		 System.out.println("음악 플레이어 ON, 볼륨:" + volume);
	 } else { System.out.println("음악 플레이어 OFF");
	 }
 }
}
```

- MusicPlayer 클래스에 음악 플레이어에 필요한 속성과 기능을 모두 정의
- 속성과 기능이 하나의 클래스에 포함

```java
package oop1;
/**
 * 객체 지향
 */
public class MusicPlayerMain4 {
 public static void main(String[] args) {
	 MusicPlayer player = new MusicPlayer();
	 //음악 플레이어 켜기
	 player.on();
	 //볼륨 증가
	 player.volumeUp();
	 //볼륨 증가
	 player.volumeUp();
	 //볼륨 감소
	 player.volumeDown();
	 //음악 플레이어 상태
	 player.showStatus();
	 //음악 플레이어 끄기
	 player.off();
 }
}
```

- MusicPlayer 객체를 생성하고 필요한 기능(메서드)을 호출하기만 하면 OK!
- MusicPlayer 를 사용하는 입장에서는 MusicPlayer 의 데이터인 volume , isOn 같은 데이터는 전혀 사용하지 않는다.
- MusicPlayer 를 사용하는 입장에서는 이제 MusicPlayer 내부에 어떤 속성(데이터)이 있는지 전혀 몰라도된다.
- MusicPlayer 를 사용하는 입장에서는 단순하게 MusicPlayer 가 제공하는 기능 중에 필요한 기능을 호출해서 사용하기만 하면 된다.

## 캡슐화

- 속성과 기능을 하나로 묶어서 필요한 기능을 메서드를 통해 외부에 제공하는 것
