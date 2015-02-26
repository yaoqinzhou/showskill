#通过指定构造器创建实例

```
public class CreateInstanceTest {

	public static void main(String[] args){
		try{
			Class<?> clazz = Class.forName("com.test.vo.Book");
			//获取参数是字符串的构造器
			Constructor<?> constructor = clazz.getConstructor(String.class);
			
		    Object obj = constructor.newInstance("think in java");
			System.out.println(obj);
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```