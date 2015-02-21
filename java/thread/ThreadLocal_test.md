#ThreadLocal 简单使用

```
public class ThreadLocalTest {

	class Account{
		private ThreadLocal<String> name = new ThreadLocal<String>();

		public Account(String name){
			this.name.set(name);
		}
		public String getName() {
			return this.name.get();
		}

		public void setName(String name) {
			this.name.set(name);
		}
	}
	
	class TestThread extends Thread{
		
		private Account account;
		
		public TestThread(Account account,String name){
			super(name);
			this.account = account;
		}
		
		public void run(){
			for(int k=0; k<10; k++){
				if(k == 5){
					account.setName(getName());
				}
				
				System.out.println(account.getName() + " k = " + k);
			}
		}
	}
	
	public static void main(String[] args){
		//虽然这里对name进行了初始化，但是这个name是属于主线程的，所以刚开始name打印都是null值，
                //直到run方法中对其重新赋值
		Account account = new ThreadLocalTest().new Account("账号A");
		
		TestThread thread1 = new ThreadLocalTest().new TestThread(account,"线程1");
		TestThread thread2 = new ThreadLocalTest().new TestThread(account,"线程2");
		
		thread1.start();
		thread2.start();
	}
}
```