#使用Proxy和InvocationHandler来生成动态代理对象

###Person接口
```
public interface Person {

	public void eat();
	
	public void sayHello(String name);
}
```

###实现InvocationHandler接口
```
public class MyInvocationHandle implements InvocationHandler{

	/**
	 * proxy表示动态代理对象，method表示正在执行的方法，args表示方法参数
	 */
	@Override
	public Object invoke(Object proxy, Method method, Object[] args)
			throws Throwable {
		
		System.out.println("正在执行的方法：" + method);
		
		if(args != null){
			for(Object obj : args){
				System.out.println("参数 " + obj);
			}
		}else{
			System.out.println("没有参数");
		}
		return null;
	}

}
```

```
public class ProxyInvocationTest {

	public static void main(String[] args){
		try{
			
			InvocationHandler handler = new MyInvocationHandle();
			
			Person person = (Person) Proxy.newProxyInstance(Person.class.getClassLoader(),
					new Class[]{Person.class}, handler);
			
			person.eat();
			person.sayHello("jack");
			
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```

