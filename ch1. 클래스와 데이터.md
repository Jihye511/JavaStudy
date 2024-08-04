# 1. 클래스와 데이터

## 클래스
- 타입을 지정하여 변수를 선언하는 것 처럼 ex. 학생(student)이라는 타입을 만들어 볼까? => 클래스
- 사용자가 직접 정의하는 사용자 정의 타입의 설계도
  
### 객체/ 인스턴스
- 설계도인 클래스를 사용하여 실제 메모리에 만들어진 실체

----
## 객체 vs 인스턴스
< 인스턴스는 객체보다 관계에 초점>

  [Example]
  
  student1은 Student의 객체이다 (x)
  
  student1은 Student의 인스턴스이다 (o)

-> 하지만 둘다 클래스에서 나온 실체라는 핵심 의미는 같아서 구분하지 않고 사용



----
## 객체 생성
### 1. 변수 선언 
Student student1 //Student 변수 선언

![image](https://github.com/user-attachments/assets/47cc8cb0-1dab-43b4-b88c-84f7adf9f064)

### 2. 객체 생성
student = new Student() //Student 인스턴스 생성

![image](https://github.com/user-attachments/assets/e356bd00-f08c-40b8-8463-db2ae5ba13bf)

### 3. 참조값 보관
student1 = x001; //Student 인스턴스 참조값 보관

![image](https://github.com/user-attachments/assets/9c830305-a83e-4531-8a33-abc42d9a5983)
- Student student1 변수는 이제 메모리에 존재하는 실제 Student 객체(인스턴스)의 참조값을 가지고 있다.
  
```java
    Student student1 = new Student(); //1. Student 객체 생성
    Student student1 = x001; //2. new Student()의 결과로 x001 참조값 반환
    student1 = x001; //3. 최종 결과
```
### 객체에 값 대입
![image](https://github.com/user-attachments/assets/986d7c8f-f405-4ca1-bbb2-83051eddb190)

### 배열 도입
- 배열에 참조값 대입
  
  ```java Student[] students = new Student[2];```

 - 배열에 객체 보관

  ```java
students[0] = student1;
students[1] = student2;
```
### 최종 그림
![image](https://github.com/user-attachments/assets/2b044db1-5019-4bb8-af0d-2f24f378adb7)
