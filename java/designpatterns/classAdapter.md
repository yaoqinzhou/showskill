#类的适配器

核心思想就是：有一个Source类，拥有一个方法，待适配，目标接口是Targetable，通过Adapter类，将Source的功能扩展到Targetable里

```
public class Source {

	public void method1() {
		System.out.println("this is original method!");
	}
}

public interface Targetable {

	/* 与原类中的方法相同 */
	public void method1();

	/* 新类的方法 */
	public void method2();
}

public class Adapter extends Source implements Targetable {

	@Override
	public void method2() {
		System.out.println("this is the targetable method!");
	}
}
```