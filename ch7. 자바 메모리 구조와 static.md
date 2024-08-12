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
