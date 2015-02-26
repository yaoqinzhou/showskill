#利用Method对象的invoke方法调用对象的方法

```
public class Book {
	private String name;
	
	public Book(String name){
		this.name = name;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		System.out.println("setName method name = " + name);
		
		this.name = name;
	}
}
```

```
public class CreateInstanceTest {

	public static void main(String[] args){
		try{
			Class<?> clazz = Class.forName("com.test.vo.Book");
			
			Constructor<?> constructor = clazz.getConstructor(String.class);
			
			Object obj = constructor.newInstance("think in java");
			
			Method method = clazz.getMethod("setName", String.class);
			
			method.invoke(obj, "effective java");
			
			System.out.println(obj);
			
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}

```