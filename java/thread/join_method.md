#�߳�join����

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
		JoinThread joinThread = new JoinThread("join�߳�");
		joinThread.start();
		
		joinThread.join();
		
		
		//���������������ִ�У���Ϊ������join������ǰ�̱߳�������
		System.out.println("��ǰ�����̣߳�"+ Thread.currentThread().getName());
	}
}
```