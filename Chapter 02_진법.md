진법
===
비트와 바이트
------
한자리의 2진수를 비트라고 하며, 1비트는 8바이트이다.

8진법과 16진법
-----
2진수를 3자리씩 끊어 그에 해당하는 8진수로 바꾸면 8진법   
4자리씩 끊어 그에 해당하는 16진수로 바꾸면 16진법   

음수의 2진 표현-2의 보수법
--------------
어떤 수의 ‘n의 보수’는 더했을 때 n이 되는 수를 말한다.
2의 보수 관계란 두 2진수를 더했을 때 10이 되는 수이고 (자리올림이 발생한)0이기도 하다.

    2의 보수 = 1의 보수 + 1

기본형
----
### 논리형 (boolean): true와 false 중 하나를 저장한다. 기본값(default)는 false

### 문자형 (char): 단 하나의 문자만을 저장한다. 저장할 문자를 유니코드 형태로 저장한다.   
그래서 문자 리터럴 대신 문자의 유니코드를 직접 저장 할 수도 있다.
* 문자형 저장하는 코드
```java
public class CharToCode {
	public static void main(String[] args) {
		char ch = 'A';
		int code = (int)ch;
		
		System.out.printf("%c = %d(%#X)%n", ch, code, code);
		
		char hch = '가';
		System.out.printf("%c = %d(%#X)%n", hch, (int)hch, (int)hch);
	}
}
```

### 정수형 (byte, short, int, long): 정수형에는 모두 4개의 자료형이 있으며, 각 자료형이 저장할 수 있는 값의 범위가 다르다.

| 1 byte | 2 byte | 4 byte | 8 byte |
|--------|--------|--------|--------|
| byte   | short  | int    | long   |

### 정수형의 오버플로우
오버플로우: 타입이 표현할 수 있는 값의 범위를 넘어서는 것
정수형 타입이 표현할 수 있는 최대값에 1을 더하면 최소값이 되고, 최소값에서 1을 빼면 최대값이 된다.
부호있는 정수의 오버플로우에선 부호비트가 0에서 1이 될 때 오버플로우가 발생한다.
* 오버플로우를 확인하는 코드
```java
public class OverflowEX {
	public static void main(String[] args) {
		short sMin = -32768;
		short sMax = 32767;
		char cMin = 0;
		char cMax = 65535;
		
		System.out.println("sMin = "+ sMin);
		System.out.println("sMin-1 = "+ (short)(sMin-1));
		System.out.println("sMax = "+ sMax);
		System.out.println("sMax+1 = "+ (short)(sMax+1));
		System.out.println("cMin = "+ (int)cMin);
		System.out.println("cMin-1 = "+ (int)--cMin);
		System.out.println("cMax = "+ (int)cMax);
		System.out.println("cMax+1 = "+ (int)++cMax);
	}
}
```
### 실수형 (float, double)
* 실수형의 범위와 정밀도

| 타입   | 저장가능한 값의 범위 (양수) | 정밀도 | 크기   |
|--------|-----------------------------|--------|--------|
| float  | 1.4*10^(-45) ~ 3.4*10^38    | 7자리  | 4 byte |
| double | 4.9*10^(-324) ~ 1.8*10^308  | 15자리 | 8 byte |

* float과 double의 정밀도를 확인하는 코드
```java
public class FloatEX1 {
	public static void main(String[] args) {
		float f = 9.12345678901234567890f;
		float f2 = 1.2345678901234567890f;
		double d = 9.12345678901234567890d;
		
		System.out.printf("     123456789012345678901234%n");
		System.out.printf("f  : %f%n", f);
		System.out.printf("f  : %24.20f%n", f);
		System.out.printf("f2 : %24.20f%n", f2);
		System.out.printf("d  : %24.20f%n", d);
	}
}
```

형변환(casting)
----
변수 또는 상수의 타입을 다른 타입으로 변환하는 것

	(타입)피연산자

피연산자인 변수의 값은 형변환 후에도 아무런 변화가 없다.
* 캐스팅 실습 코드
```java
public class CastingEX {
	public static void main(String[] args) {
		double d = 85.4;
		int score = (int)d;
		
		System.out.println("score="+score);
		System.out.println("d="+d);
	}
}
```
