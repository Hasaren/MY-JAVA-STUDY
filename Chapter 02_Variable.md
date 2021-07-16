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

'''java
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
'''
