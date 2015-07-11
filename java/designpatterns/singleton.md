#单例模式

###双重校验锁方式

将synchronized关键字加在了内部，也就是说当调用的时候是不需要加锁的，只有在instance为null，
并创建对象的时候才需要加锁，性能有一定的提升。但是，这样的情况，还是有可能有问题的，在Java指令中创建对象和赋值操作是分开进行的，
也就是说instance = new Singleton()语句是分两步执行的。但是JVM并不保证这两个操作的先后顺序，
也就是说有可能JVM会为新的Singleton实例分配空间，然后直接赋值给instance成员，然后再去初始化这个Singleton实例

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