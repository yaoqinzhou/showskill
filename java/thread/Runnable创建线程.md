#Runnable接口创建线程类

```
public class Test01 {

	public static void main(String[] args){
		Thread1 thread1 = new Test01().new Thread1();
		
		new Thread(thread1,"线程1").start();
		new Thread(thread1,"线程2").start();
	}
	//用多线程对同一个数组求和
	class Thread1 implements Runnable{
		private int[] aa = new int[300];
		
		private int sum = 0;
		
		private int n = 0;
			
		public Thread1(){
			for(int i=0; i<300; i++){
				aa[i] = 2;
			}
		}
		
		@Override
		public void run() {
			for(int k=0; k<50; k++){
				sum += aa[n];
				n++;
				
				System.out.println("Thread name = " + Thread.currentThread().getName()
						+ " sum = " + sum + " n = " + n);
			}	
		}
	}
	
}
```