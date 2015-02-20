#ReentrantLock示例

```
public class Test03 {

	private final ReentrantLock lock = new ReentrantLock();
	
	public void test(){
		//加锁
		lock.lock();
		
		try{
			//这里是线程安全的代码块
			
		}finally{
			//使用finally块来保证释放锁
			lock.unlock();
		}
	}
}
```