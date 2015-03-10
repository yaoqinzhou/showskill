#单例模式

###双重校验锁方式
```
public class Singleton {

	private static volatile Singleton instance = null;
	
	private Singleton() {};
	
	public static Singleton getInstance(){
		if(instance == null){
			synchronized(Singleton.class){
				instance = new Singleton();
				return instance;
			}
		}else{
			return instance;
		}
	}
}
```