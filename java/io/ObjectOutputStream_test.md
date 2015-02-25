#使用ObjectOutputStream序列化对象到文件中

##Person类实现Serializable接口

```
public class Person implements Serializable{
	
	private static final long serialVersionUID = 1L;
	
	private String name;
	
	public Person(String name){
		this.name = name;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}
}
```

##将对象写入文件中

```
public class ObjectOutputStreamTest {
	
	public static void main(String[] args){
		try{
			Person person = new Person("jack");
			
			ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("object.txt"));
			
			oos.writeObject(person);
			
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```