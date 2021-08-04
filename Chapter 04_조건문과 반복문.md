Chapter 04 조건문과 반복문
====
조건문 - if, switch
----
조건문은 조건식과 실행문을 묶어둔 { }로 이루어져 있다. 조건식의 연산결과에 따라 실행할 문장이 달라져서 프로그램의 실행흐름을 원하는 대로 만들 수 있다.

#### if문
    만일(if) 조건식이 참(true)이면 { } 안의 문장들을 실행하라.

```
if (조건식) {
	// 조건식이 참일 때 수행될 문장들
}
```
* 방문 횟수가 1보다 작으면 환영 인사를 하는 코드
```java
public class FlowEX1 {
	public static void main(String[] args) {
		int visitCount = 0;
		if (visitCount < 1) {
			System.out.println("처음 오셨군요. 방문해 주셔서 감사합니다.");
		}
	}
}
```
```
처음 오셨군요. 방문해 주셔서 감사합니다.
```
* 조건문의 { }여부에 따른 변화를 확인하는 코드
```java
import java.util.*;
public class FlowEX2_1 {
	public static void main(String[] args) {
		int input;
		
		System.out.print("숫자를 하나 입력하세요. >");
		
		Scanner scanner = new Scanner(System.in);
		String tmp = scanner.nextLine();
		input = Integer.parseInt(tmp);
		
		if(input==0) {
			System.out.println("입력하신 숫자는 0입니다.");
		}
		if(input!=0) 
			System.out.println("입력하신 숫자는 0이 아닙니다.");
			System.out.printf("입력하신 숫자는 %d입니다.", input);
	}
}
```
```
숫자를 하나 입력하세요. >3
입력하신 숫자는 0이 아닙니다.
입력하신 숫자는 3입니다.
```
```
숫자를 하나 입력하세요. >0
입력하신 숫자는 0입니다.
입력하신 숫자는 0입니다.
```

#### if-else문
    만일(if) 조건식의 결과가 참일 때(true) { } 안의 문장을, 참이 아닐 때(false) else { } 안의 문장을 수행하라.
```
if (조건식) {
	// 조건식이 참일 때 수행될 문장들
} else {
	// 조건식이 거짓일 때 수행될 문장들
}
```
* FlowEX2_1에서 따로 지정한 조건을 if-else문으로 묶은 코드
```java
import java.util.Scanner;
public class FlowEX3_1 {
	public static void main(String[] args) {
		int input;
		
		System.out.print("숫자를 하나 입력하세요. >");
		
		Scanner scanner = new Scanner(System.in);
		String tmp = scanner.nextLine();
		input = Integer.parseInt(tmp);
		
		if(input==0) {
			System.out.println("입력하신 숫자는 0입니다.");
		} else {
			System.out.println("입력하신 숫자는 0이 아닙니다.");
		}
	}
}
```

#### if-else if문
    만일(if) 조건식의 결과가 참일 때 { } 안의 문장을, 다른 조건식의 결과가 참일 때 else if { } 안의 문장을 수행하라.
```
if (조건식1) {
	// 조건식1이 참일 때 수행될 문장들
} else if (조건식2) {
	// 조건식2이 참일 때 수행될 문장들
} else if (조건식3) {
	// 조건식3이 참일 때 수행될 문장들
}
```
* 특정 점수일 때 등급을 표시하는 코드
```java
public class FlowEX3 {
	public static void main(String[] args) {
		int score = 45;
		char grade = '\u0000';
		
		if(score >=90) {
			grade='A';
		} else if (score >= 80) {
			grade = 'B';
		} else {
			grade = 'C';
		}
		System.out.println("당신의 학점은 " + grade + "입니다.");
	}
}
```
```
당신의 학점은 C입니다.
```
* 조건 연산자 조건식 ? 식1: 식2 로 표현한 코드
```java
public class FlowEX4 {
	public static void main(String[] args) {
		int score = 45;
		char grade = '\u0000';
		grade = (score >= 90) ? 'A':((score >=80) ? 'B':'C');
		
		System.out.println("당신의 학점은 "+grade+"입니다.");
	}
}
```
```
당신의 학점은 C입니다.
```

#### 중첩 if문
    if문 안에 if문을 포함시킬 수 있다. 중첩의 횟수는 제한이 없다.
```
if (조건문1) {
	// 조건문1만 참일 때 수행될 문장들
	if (조건문2) {
		// 조건문1과 조건문2가 모두 참일 때 수행될 문장들
	} else {
		// 조건문1은 참이고 조건문2는 거짓일 때 수행될 문장들
	}
} else {
	// 조건문1이 거짓일 때 수행될 문장들
}
```
* 점수에 따라 등급을 나누고 세부적으로 한번더 세부등급을 나누는 코드
```java
public class FlowEX5 {
	public static void main(String[] args) {
		int score = 82;
		String grade="";
		
		System.out.println("당신의 점수는"+score+"입니다.");
		if (score >= 90) {
			grade="A";
			if (score >= 98) {
				grade += "+";
			} else if (score <94) {
				grade += "-";
			}
		} else if (score >= 80) {
			grade = "B";
			if (score >=88) {
				grade += "+";
			} else if (score <84) {
				grade += "-";
			}
		} else {
			grade = "C";
		}
		System.out.println("당신의 학점은 "+grade+"입니다.");
	}
}
```
```
당신의 점수는82입니다.
당신의 학점은 B-입니다.
```

#### switch문
단 하나의 조건식으로 많은 경우의 수를 처리할 수 있다.
* 처리과정
1. 조건식을 계산한다.
2. 조건식의 결과와 일치하는 case문으로 이동한다.
3. 이후의 문장들을 수행한다.
4. break문이나 switch문의 끝을 만나면 switch문 전체를 빠져나간다.

```
switch (조건식) {
	case 값1:
		// 조건식의 결과가 값1과 같을 경우 수행될 문장들
		//...
		break;
	case 값2:
		// 조건식의 결과가 값2과 같을 경우 수행될 문장들
		//...
		break;
	//...
	default:
		// 조건식의 결과가 일치하는 case문이 없을 때 수행될 문장들
		//..
}
```
* switch문의 제약조건
1. switch문의 조건식 결과는 정수 또는 문자열이어야 한다.
2. case문의 값은 정수 상수만 가능하며, 중복되지 않아야 한다.

* 랜덤으로 나오는 점수에 따라 경품을 알려주는 코드
```java
public class FlowEX6 {
	public static void main(String[] args) {
		int score = (int)(Math.random()*10)+1;
		
		switch(score*100) {
		case 100:
			System.out.println("당신의 점수는 100이고, 상품은 자전거입니다.");
			break;
		case 200:
			System.out.println("당신의 점수는 200이고, 상품은 TV입니다.");
			break;
		case 300:
			System.out.println("당신의 점수는 300이고, 상품은 노트북입니다.");
			break;
		case 400:
			System.out.println("당신의 점수는 400이고, 상품은 자동차입니다.");
			break;
		default:
			System.out.println("죄송하지만 당신의 점수에 해당하는 상품이 없습니다.");
		}
	}
}
```
```
당신의 점수는 300이고, 상품은 노트북입니다.
```
* case문을 연달아 쓰면 여러 경우에 같은 문장을 수행하는 코드
```java
import java.util.*;
public class FlowEX7_1 {
	public static void main(String[] args) {
		System.out.print("현재 월을 입력하세요.>");
		
		Scanner scanner = new Scanner(System.in);
		int month = scanner.nextInt();
		
		switch (month) {
		case 3:
		case 4:
		case 5:
			System.out.println("현재의 계절은 봄입니다.");
			break;
		case 6: case 7: case 8:
			System.out.println("현재의 계절은 여름입니다.");
			break;
		case 9: case 10: case 11:
			System.out.println("현재의 계절은 가을입니다.");
			break;
		default:
		case 12: case 1: case 2:
			System.out.println("현재의 계절은 겨울입니다.");
		
		}
	}
}
```
```
현재 월을 입력하세요.> 8
현재의 계절은 여름입니다.
```

#### Math.random() 사용하기
Math.random()은 0.0은 포함하고 1.0은 포함하지 않는다.
만약 1과 10 사이의 정수를 구하기를 원한다면 다음 과정을 거친다.
1. 각 변에 10을 곱한다.
```
3.0 * 10 <= Math.random() * 10 < 1.0 * 10   
4.0 <= Math.random() * 10 < 10.0
```
2. 각 변을 int형으로 변환한다.
```
(int)0.0 <= (int)(Math.random() * 10) < (int)10.0   
0 <= (int)(Math.random() * 10) < 10
```
3. 각 변에 1을 더한다.
```
0 + 1 <= (int)(Math.random() * 10) + 1 < 10 + 1   
1 <= (int)(Math.random() * 10) + 1 < 11
```

#### switch문의 중첩
switch문도 중첩이 가능하다.
* 주민등록번호로 성별과 출생시기를 알려주는 코드
```java
import java.util.*;
public class FlowEX11 {

	public static void main(String[] args) {
		System.out.print("당신의 주민번호를 입력하세요. (011231-1111222)>");
		
		Scanner scanner = new Scanner(System.in);
		String regNo = scanner.nextLine();
		char gender = regNo.charAt(7);
		
		switch (gender) {
		case '1': case '3':
			switch (gender) {
			case '1':
				System.out.println("당신은 2000년 이전에 출생한 남자입니다.");
				break;
			case '3':
				System.out.println("당신은 2000년 이후에 출생한 남자입니다.");
				break;
			}
			break;
		case '2': case '4':
			switch (gender) {
			case '2':
				System.out.println("당신은 2000년 이전에 출생한 여자입니다.");
				break;
			case '4':
				System.out.println("당신은 2000년 이후에 출생한 여자입니다.");
				break;
			}
			break;
		default:
			System.out.println("유효하지 않은 주민등록번호입니다.");
		}
	}
}
```
```
당신의 주민번호를 입력하세요. (011231-1111222)>000413-1234123
당신은 2000년 이전에 출생한 남자입니다.
```

반복문
----
어떤 작업이 반복적으로 수행되도록 한다.
#### for문
```java
for (int i=1; i<=5; i++) {
	System.out.println("I can do it."); 
}
```
```
for (초기화; 조건식; 증감식) {
	// 조건식이 참일 때 수행될 문장들
}
```

#### 초기화
반복문에 사용될 변수를 초기화한다. 같은 타입의 두 변수로도 for문을 제어할 수 있다.
for (int i=1; i<=10; i++) {...}
for (int i=1, j=0; i<=10; i++) {...}

#### 조건식
조건식이 참이면 반복을 계속하고 거짓이면 반복을 중단하고 for문을 벗어난다.

#### 증감식
반복문을 제어하는 변수의 값을 증가 또는 감소시킨다. 매 반복마다 변수의 값이 변하다가 결국 조건식이 거짓이 되어 for문을 벗어나게 된다.
    
    for (int i=1; i<=10; i++) {...}  // 1부터 10까지 1씩 증가
    for (int i=10; i>=1; i--) {...}  // 10부터 1까지 1씩 감소
    for (int i=1; i<=10; i+=2) {...}  // 1부터 10까지 2씩 증가
    for (int i=1; i<=10; i*=3) {...}  // 1부터 10까지 3배씩 증가
    for (int i=1, j=10; i<=10; i++, j--) {...}  // i는 10까지 1씩 증가, j는 10부터 1씩 감소
    for (;;) {...} // 무한 반복문

* i가 10까지 1씩 증가하면서 i값을 더하는 반복문
```java
public class FlowEX12 {
	public static void main(String[] args) {
		int sum = 0;
		
		for (int i=1; i <= 10; i++) {
			sum +=i;
			System.out.println(i+"까지의 합: "+sum);
		}
	}
}
```
```
1까지의 합: 1
2까지의 합: 3
3까지의 합: 6
4까지의 합: 10
5까지의 합: 15
6까지의 합: 21
7까지의 합: 28
8까지의 합: 36
9까지의 합: 45
10까지의 합: 55
```

#### 중첩 for문
for문 안에 또 다른 for문을 포함시킬 수 있다. 중첩의 횟수는 제한이 없다.
* 사용자로부터 라인의 수를 입력받아 별을 출력하는 코드
```java
import java.util.*;
public class FlowEX17 {
	public static void main(String[] args) {
		int num = 0;
		System.out.print("*을 출력할 라인의 수를 입력하시오. > ");
		
		Scanner scanner = new Scanner(System.in);
		String tmp = scanner.nextLine();
		num = Integer.parseInt(tmp);
		
		for(int i=0;i<num;i++) {
			for(int j=0;j<=i;j++) {
				System.out.print("*");
			}
			System.out.println();
		}
	}
}
```
```
*을 출력할 라인의 수를 입력하시오. > 5
*
**
***
****
*****
```

#### 향상된 for문
배열과 컬렉션에 저장된 요소에 접근할 때 기존보다 편리한 방법으로 처리할 수 있다.
```
for(타입 변수명 : 배열 또는 컬렉션) {
	// 반복할 문장
}
```
* 정수 배열을 차례로 출력하고 순서대로 더하는 코드
```java
public class FlowEX22 {
	public static void main(String[] args) {
		int[] arr = {10, 20, 30, 40, 50};
		int sum = 0;
		
		for(int i=0;i<arr.length;i++)
			System.out.printf("%d ", arr[i]);
		System.out.println();
		
		for(int tmp : arr) {
			System.out.printf("%d ", tmp);
			sum += tmp;
		}
		System.out.println();
		System.out.println("sum= "+sum);
	}
}
```
```
10 20 30 40 50 
10 20 30 40 50 
sum= 150
```

#### while문
```
while (조건식) {
	// 조건식의 연산 결과가 참인 동안, 반복될 문장
}
```
while문은 조건식을 생략할 수 없다.

* 1초마다 카운트 다운을 하는 코드
```java
public class FlowEX24 {
	public static void main(String[] args) {
		int i = 6;
		
		System.out.println("카운트다운 시작");
		while (i--!=0) {
			System.out.println(i);
			
			for(int j=0;j<2_000_000_000;j++) {
				;
			}
		}
		System.out.println("Game Over");
	}
}
```
```
카운트다운 시작
5
4
3
2
1
0
Game Over
```

#### do-while문
while문의 변형으로 기본적인 while문의 구조의 순서를 반대로 바꿔놓았다.
```
do {
	// 조건식의 연산결과가 참일 때 수행될 문장
} while (조건식);
```
* 반복적으로 사용자의 입력을 받아서 처리하는 코드
```java
import java.util.*;
public class FlowEX28 {
	public static void main(String[] args) {
		int input = 0, answer = 0;
		
		answer = (int)(Math.random() * 100) + 1;
		Scanner scanner = new Scanner(System.in);
		
		do {
			System.out.print("1과 100 사이의 정수를 입력하시오. > ");
			input = scanner.nextInt();
			
			if(input> answer) {
				System.out.println("더 작은 수로 다시 시도하세요.");
			}else if(input< answer) {
				System.out.println("더 큰 수로 다시 시도하세요.");
			}
		}while(input!=answer);
		System.out.println("정답입니다.");
	}
}
```
```
1과 100 사이의 정수를 입력하시오. > 50
더 큰 수로 다시 시도하세요.
1과 100 사이의 정수를 입력하시오. > 70
더 큰 수로 다시 시도하세요.
1과 100 사이의 정수를 입력하시오. > 90
더 큰 수로 다시 시도하세요.
1과 100 사이의 정수를 입력하시오. > 100
정답입니다.
```

#### break문
자신이 포함된 가장 가까운 반복문을 벗어난다. 주로 if문과 함께 사용되어 특정 조건이 되면 반복문을 벗어나게 만들 수 있다.
* 숫자를 반복하여 더하다가 합이 100을 넘지 않도록 하는 코드
```java
public class FlowEX30 {
	public static void main(String[] args) {
		int sum = 0;
		int i = 0;
		
		while (true) {
			if(sum>100)
				break;
			i++;
			sum +=i;
		}
		System.out.println("i= " + i);
		System.out.println("sum= " + sum);
	}
}
```
```
i= 14
sum= 105
```

#### continue문
반복이 진행되는 도중 continue문을 만나면 반복문의 끝으로 이동하여 다음 반복으로 넘어간다.
* 키오스크 메뉴를 선택하게 하는 코드
```java
import java.util.*;
public class FlowEX32 {
	public static void main(String[] args) {
		int menu = 0;
		int num = 0;
		Scanner scanner = new Scanner(System.in);
		
		while(true) {
			System.out.println("(1) square");
			System.out.println("(2) square rood");
			System.out.println("(3) log");
			System.out.print("원하는 메뉴(1~3)를 선택하세요. (종료: 0) >");
			
			String tmp = scanner.nextLine();
			menu = Integer.parseInt(tmp);
			
			if(menu==0) {
				System.out.println("프로그램을 종료합니다.");
				break;
			} else if (!(1 <= menu && menu <= 3)) {
				System.out.println("메뉴를 잘못 선택하셨습니다. (종료: 0)");
				continue;
			}
			System.out.println("선택하신 메뉴는 "+menu+"번 입니다.");
		}
	}
}
```
```
(1) square
(2) square rood
(3) log
원하는 메뉴(1~3)를 선택하세요. (종료: 0) >4
메뉴를 잘못 선택하셨습니다. (종료: 0)
(1) square
(2) square rood
(3) log
원하는 메뉴(1~3)를 선택하세요. (종료: 0) >1
선택하신 메뉴는 1번 입니다.
(1) square
(2) square rood
(3) log
원하는 메뉴(1~3)를 선택하세요. (종료: 0) >0
프로그램을 종료합니다.
```
