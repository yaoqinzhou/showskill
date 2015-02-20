#线程调用Yield方法

```
public class YieldThread extends Thread{
	public YieldThread(String name){
		super(name);
	}
	
	public void run(){
		for(int k=0;k<50;k++){
			System.out.println("thread name :" + getName() + " k = " + k);
			
			if(k == 20){
				Thread.yield();
			}
		}
	}
	/**
	 * 当线程不设置优先级的话，线程优先级是相等的，这样的话一个线程调用yield方法后另一个线程就会被执行，
	 * 如果设置了优先级，那么优先级高的线程调用yield方法后，优先级低的线程也不会被执行
	 */
	public static void main(String[] args) throws Exception{
		YieldThread yield1 = new YieldThread("高级");
		//yield1.setPriority(Thread.MAX_PRIORITY);

		YieldThread yield2 = new YieldThread("低级");
		//yield2.setPriority(Thread.MIN_PRIORITY);
		
		yield1.start();
		yield2.start();

	}
}
```