#�̵߳���Yield����

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
	 * ���̲߳��������ȼ��Ļ����߳����ȼ�����ȵģ������Ļ�һ���̵߳���yield��������һ���߳̾ͻᱻִ�У�
	 * ������������ȼ�����ô���ȼ��ߵ��̵߳���yield���������ȼ��͵��߳�Ҳ���ᱻִ��
	 */
	public static void main(String[] args) throws Exception{
		YieldThread yield1 = new YieldThread("�߼�");
		//yield1.setPriority(Thread.MAX_PRIORITY);

		YieldThread yield2 = new YieldThread("�ͼ�");
		//yield2.setPriority(Thread.MIN_PRIORITY);
		
		yield1.start();
		yield2.start();

	}
}
```