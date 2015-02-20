#线程join方法

```
public class JoinThread extends Thread{

	public JoinThread(String name){
		super(name);
	}
	
	public void run(){
		for(int k=0; k<50; k++){
			System.out.println("threadName: " + getName() + " k = "+k);
		}
	}
	
	public static void main(String[] args) throws Exception{
		JoinThread joinThread = new JoinThread("join线程");
		joinThread.start();
		
		joinThread.join();
		
		
		//下面的输出会在最后执行，因为调用了join方法当前线程被阻塞了
		System.out.println("当前是主线程："+ Thread.currentThread().getName());
	}
}
```