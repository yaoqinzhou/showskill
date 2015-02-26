#利用Field对象访问属性

###Person对象
```
public class Person{
	//属性都是私有的
	private String name;

	private int age;
	
	public String toString(){
		return "Person name:" + name + " age:" + age;
	}
}
```

```
public class CreateInstanceTest {

	public static void main(String[] args){
		try{
			Class<?> clazz = Class.forName("com.test.vo.Person");
			Object obj = clazz.newInstance();
			
			Field nameField = clazz.getDeclaredField("name");
			//去掉java的访问权限检查
			nameField.setAccessible(true);
			nameField.set(obj, "jack");
			
			Field ageField = clazz.getDeclaredField("age");
			ageField.setAccessible(true);
			ageField.setInt(obj, 32);
			
			System.out.println(obj);
			
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```