#将标准输出重定向到PrintStream输出流

```
public class RedirectOut {

	public static void main(String[] args){
		try{
			PrintStream ps = new PrintStream("redirect.txt");
			//将标准输出重定向到printstream输出流
			System.setOut(ps);
			
			System.out.println("print into");
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```