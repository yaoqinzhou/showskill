#ReentrantLockʾ��

```
public class Test03 {

	private final ReentrantLock lock = new ReentrantLock();
	
	public void test(){
		//����
		lock.lock();
		
		try{
			//�������̰߳�ȫ�Ĵ����
			
		}finally{
			//ʹ��finally������֤�ͷ���
			lock.unlock();
		}
	}
}
```