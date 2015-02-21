#<T> Future<T> submit(Callable<T> task) 示例

```
public class CallableThread implements Callable<Integer>{

	@Override
	public Integer call() throws Exception {
		return 20;
	}
	
	public static void main(String[] args) throws Exception{
		CallableThread task = new CallableThread();

		ExecutorService service = Executors.newCachedThreadPool();
		
		Future<Integer> future = service.submit(task);
		
		System.out.println("返回值：" + future.get());
	}

}
```