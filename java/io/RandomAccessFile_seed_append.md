#通过RandomAccessFile的seed方法给文件追加内容

```
public class RandomAccessFileAppend {

	public static void main(String[] args){
		try{
			RandomAccessFile raf = new RandomAccessFile("filewriter.txt","rw");
			
			raf.seek(raf.length());
			
			raf.write("通过raf追加的内容\r\n".getBytes());

		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
}
```