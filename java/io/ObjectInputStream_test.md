#利用ObjectInputStream反序列化

```
public class ObjectInputStreamTest {

	public static void main(String[] args){
		try{
			ObjectInputStream ois = new ObjectInputStream(new FileInputStream("object.txt"));
			
			Person person = (Person)ois.readObject();
			
			System.out.println(person.getName());
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```