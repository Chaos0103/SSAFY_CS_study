# 싱글턴 패턴
### 싱글턴 패턴이란?
생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나이고 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴하는 패턴을 **'싱글턴 패턴'** 이라고 한다. 주로 공통된 객체를 생성해서 사용하는 DBCP(DataBase Connection Pool)와 같은 상황에서 많이 사용된다.

```
public class Singleton {
	private static Singleton counseler = new Singleton();
	
	private Singleton() {}
	
	public static Singleton getInstance() {
		return counseler;
	}
	
	private static boolean calling = false;
	
	public static void call() {
		calling = true;
		System.out.println("상담원과 연결되었습니다.");
	}
	
	public static void waiting() {
		calling = false;
		System.out.println("상담원이 전화중입니다.");
	}
	
	public static boolean canCall() {
		return !calling;
	}
	
	public static void main(String[] args) {
		Singleton user1 = Singleton.getInstance();
		Singleton user2 = Singleton.getInstance();
		
		if (canCall()) {
			user1.call();
		} else {
			user1.waiting();
		}
		
		if(canCall()) {
			user2.call();
		} else {
			user2.waiting();
		}
	}
}
```
#### 출력결과
상담원과 연결되었습니다.
상담원이 전화중입니다.

싱글턴 패턴은 요청이 많은 곳에서 사용하게 된다면, 메모리에 객체를 하나만 올려놓기 때문에 데이터 효율을 높일 수 있다.
