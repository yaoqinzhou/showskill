#动态代理实现AOP

###Dog接口
```
public interface Dog {
	public void info();
	
	public void run();
}
```

###Dog接口实现类
```
public class MyDog implements Dog{

	@Override
	public void info() {
		System.out.println("这是我的狗");
	}

	@Override
	public void run() {
		System.out.println("它正在奔跑");
	}
}
```

###公共方法
```
public class CommonUtil {

	public void before(){
		System.out.println("执行before方法");
	}
	
	public void after(){
		System.out.println("执行after方法");
	}
}
```

###InvocationHandler接口实现类
```
public class MyInvocationHandle implements InvocationHandler{
	
	private Object target;
	
	public MyInvocationHandle(Object target){
		this.target = target;
	}

	/**
	 * proxy表示动态代理对象，method表示正在执行的方法，args表示方法参数
	 */
	@Override
	public Object invoke(Object proxy, Method method, Object[] args)
			throws Throwable {
		
		CommonUtil commonUtil = new CommonUtil();
		
		commonUtil.before();
		
		//调用目标对象方法
		Object result = method.invoke(target, args);
		
		commonUtil.after();
		
		return result;
	}
}
```

###工厂类
```
public class MyProxyFactory {

	public static Object getProxy(Object target) throws Exception{
		MyInvocationHandle handler = new MyInvocationHandle(target);
		
		//返回一个动态代理
		return Proxy.newProxyInstance(target.getClass().getClassLoader(),
				target.getClass().getInterfaces(), handler);
	}
}
```

###调用

```
public class ProxyInvocationTest {

	public static void main(String[] args){
		try{
			Dog target = new MyDog();
			
			Dog dog = (Dog)MyProxyFactory.getProxy(target);
			
			dog.run();
			dog.info();
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```