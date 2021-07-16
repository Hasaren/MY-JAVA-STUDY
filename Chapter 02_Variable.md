Chapter 02 변수
===============
변수란?
--------
값을 저장할 수 있는 메모리상의 공간. 
변수를 선언하면 메모리에 데이터를 저장할 수 있는 자리가 마련된다.

선언과 초기화
-------------
변수는 “변수타입 변수이름;”으로 선언한다.
변수타입에 알맞은 크기의 저장공간이 확보되고, 앞으로 이 저장공간은 변수이름을 통해 사용할 수 있게 된다.

초기화: 변수를 사용하기 전에 처음으로 값을 저장하는 것
변수는 반드시 초기화 해야한다. 알 수 없는 값, 쓰레기 값이 저장되어 있을 수 있기 때문이다. 

* 변수를 선언, 초기화하고 저장된 값을 읽어오는 코드
```java
public class varEX1 {
	public static void main(String[] args) {
		int year = 0;
		int age = 14;
		
		System.out.println(year);
		System.out.println(age);
		
		year = age + 2000;
		age = age + 1;
		
		System.out.println(year);
		System.out.println(age);
	}
}
```
* 두 변수의 값을 교환하는 코드
```java
public class varEX2 {
	public static void main(String[] args) {
		int x = 10, y = 20;
		int tmp = 0;
		
		System.out.println("x = " + x + " y =" + y);
		
		tmp = x;
		x = y;
		y = tmp;
		
		System.out.println("x = " + x + " y =" + y);
	}
}
```

변수의 명명규칙
-----------
1. 대소문자가 구분되며 길이에 제한이 없다.
2. 예약어를 사용해서는 안 된다.
3. 숫자로 시작해서는 안 된다.
4. 특수문자는 _ 와 $만을 허용한다.

변수의 타입
----------
기본형: 실제 값(data)을 저장, 논리형, 문자형, 정수형, 실수형으로 총 8개
참조형: 어떤 값이 저장되어 있는 주소(memory address)를 저장, 8개의 기본형을 제회한 나머지

기본 자료형의 종류와 크기
--------------------
||1byte|2byte|4byte|8byte|
|--------|--------|--------|--------|--------|
|논리형  |boolean |        |        |        |
|문자형  |        |char    |        |        |
|정수형  |byte    |short   |int     |long    |
|실수형  |        |        |float   |double  |

상수와 리터럴
---------
상수: 변수와 달리 한번 값을 저장하면 다른 값으로 변경할 수 없다.
상수는 반드시 선언과 동시에 초기화해야 한다.

	final 변수타입 변수이름 = 값;

리터럴: 우리가 알고 있는 상수의 다른 이름. 값(data) 그자체를 의미.   
* 리터럴의 타입(값의 타입)과 접미사

||리터럴|접미사|
|--------|--------|--------|
|논리형  |false, true |        |
|정수형  |123, 0b0101, 077, 0xFF, 100L|L    |
|실수형  |3.14, 3.0e8, 1.4f, 0x1.op-1|f, d   |
|문자형  |‘A’, ‘1’, ‘\n’|        |
|문자열  |“ABC”, “123”, “A”, “true”|        |

* 문자열 리터럴을 조합하는 코드
```java
public class StringEX {
	public static void main(String[] args) {
		String name = "Ja"+"va";
		String str = name + 0.8;
		
		System.out.println(name);
		System.out.println(str);
		System.out.println(7+" ");
		System.out.println(" "+7);
		System.out.println(7+"");
		System.out.println(""+7);
		System.out.println(""+"");
		System.out.println(7+7+"");
		System.out.println(""+7+7);
	}
}
```
