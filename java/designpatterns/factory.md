#���󹤳�ģʽ

���������������һ�����ܣ�����ʱ��Ϣ����ֻ����һ��ʵ���࣬ʵ��Sender�ӿڣ�
ͬʱ��һ�������࣬ʵ��Provider�ӿڣ���OK�ˣ�����ȥ�Ķ��ֳɵĴ��롣����������չ�ԽϺã�

```
public interface Sender {
	public void Send();
}

public class MailSender implements Sender {
	@Override
	public void Send() {
		System.out.println("this is mailsender!");
	}
}

public class SmsSender implements Sender {

	@Override
	public void Send() {
		System.out.println("this is sms sender!");
	}
}

public class SendMailFactory implements Provider {
	
	@Override
	public Sender produce(){
		return new MailSender();
	}
}

public class SendSmsFactory implements Provider{

	@Override
	public Sender produce() {
		return new SmsSender();
	}
}

public interface Provider {
	public Sender produce();
}

public class Test {

	public static void main(String[] args) {
		Provider provider = new SendMailFactory();
		Sender sender = provider.produce();
		sender.Send();
	}
}
```