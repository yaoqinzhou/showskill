#内部类单例模式

###双重校验锁方式
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