#内部类单例模式


这种方式创建的话，如果在构造函数中抛出异常，实例将永远得不到创建

```
public class StaticSingleton {

	private StaticSingleton(){};
	
	private static class SingletonHolder{
		private static StaticSingleton instance = new StaticSingleton();
	}

	public static StaticSingleton getInstance(){
		return SingletonHolder.instance;
	}
}
```