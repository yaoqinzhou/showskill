#回调

###定义一个接口
```
public interface Teachable {
	void work();
}
```

###相同方法名的类
```
public class Programmer {
	public void work(){
		System.out.println("coding");
	}
}
```

###实现类
```
public class TeachableProgrammer extends Programmer{

	private class Closure implements Teachable{

		@Override
		public void work() {
			System.out.println("teacher");
		}
	}
	
	public Teachable getCallbackReference(){
		return new Closure();
	}
	
	public static void main(String[] args){
		TeachableProgrammer tp = new TeachableProgrammer();
		
		tp.work();
		
		tp.getCallbackReference().work();
	}
}
```