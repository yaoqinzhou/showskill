#<T> Future<T> submit(Runnable task,T result)示例

```
public class RunnableThread implements Runnable{
	
	public void run(){
		System.out.println("thread name:" + Thread.currentThread().getName() + " start");
	}
	
	public static void main(String[] args) throws Exception{
		
		RunnableThread runnableThread = new RunnableThread();
		
		ExecutorService service = Executors.newCachedThreadPool();
		
		Future future = service.submit(runnableThread, "runnableThread返回值");
		
		System.out.println("future返回值：" + future.get());
	}
}
```