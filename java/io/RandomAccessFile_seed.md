#RandomAccessFile seed操作

```
public class RandomAccessFileTest {

	public static void main(String[] args){
		try{
			
			String path = RandomAccessFileTest.class.getResource("/").getFile() 
					+ "../src/com/test/file/RandomAccessFileTest.java";
			
			RandomAccessFile raf = new RandomAccessFile(path,"r");
			
			raf.seek(300);
			
			byte[] buf = new byte[1024];
			
			int hasRead = 0;
			
			while((hasRead = raf.read(buf)) > 0){
				System.out.println(new String(buf,0,hasRead));
			}
			
			
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```