#桥接模式

桥接模式就是把事物和其具体实现分开，使他们可以各自独立的变化。
桥接的用意是：将抽象化与实现化解耦，使得二者可以独立变化

```
public interface Sourceable {
	public void method();
}

public class SourceSub1 implements Sourceable {

	@Override
	public void method() {
		System.out.println("this is the first sub!");
	}
}

public class SourceSub2 implements Sourceable {

	@Override
	public void method() {
		System.out.println("this is the second sub!");
	}
}

//定义一个桥，持有Sourceable的一个实例

public abstract class Bridge {
	private Sourceable source;

	public void method(){
		source.method();
	}
	
	public Sourceable getSource() {
		return source;
	}

	public void setSource(Sourceable source) {
		this.source = source;
	}
}

public class MyBridge extends Bridge {
	public void method(){
		getSource().method();
	}
}

public class BridgeTest {
	
	public static void main(String[] args) {
		
		Bridge bridge = new MyBridge();
		
		/*调用第一个对象*/
		Sourceable source1 = new SourceSub1();
		bridge.setSource(source1);
		bridge.method();
		
		/*调用第二个对象*/
		Sourceable source2 = new SourceSub2();
		bridge.setSource(source2);
		bridge.method();
	}
}
```