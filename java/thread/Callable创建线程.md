#Callable接口和FutureTask类创建线程

```
public class Test02 {

	public static void main(String[] args) throws Exception{
		Thread2 thread2 = new Test02().new Thread2();
		
		FutureTask<Integer> task = new FutureTask<Integer>(thread2);
		
		new Thread(task,"线程1").start();
		
		System.out.println("sum = " + task.get());

	}
	//返回数组的总和
	class Thread2 implements Callable<Integer>{
		private int[] aa = new int[300];
		
		private int sum = 0;
		
		private int n = 0;
			
		public Thread2(){
			for(int i=0; i<300; i++){
				aa[i] = 2;
			}
		}
		
		@Override
		public Integer call() throws Exception {
			
			for(int k=0; k<aa.length; k++){
				sum += aa[n];
				n++;
				
				System.out.println("Thread name = " + Thread.currentThread().getName()
						+ " sum = " + sum + " n = " + n);
			}	
			
			return sum;
		}
		
	}
}
```