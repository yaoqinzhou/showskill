#利用RandomAccessFile在文件的指定位置插入内容

```
public class RandomAccessFileInsert {

	public static void main(String[] args){
		try{
			insertContent("filewriter.txt",0,"最新插入的内容");
		}catch(Exception ex){
			ex.printStackTrace();
		}
	}
	
	public static void insertContent(String fileName,long pos,String content) 
		throws Exception{
		
		File tmp = File.createTempFile("tmp", null);
		tmp.deleteOnExit();
		
		RandomAccessFile raf = new RandomAccessFile(fileName,"rw");
		
		FileOutputStream fos = new FileOutputStream(tmp);
		FileInputStream fis = new FileInputStream(tmp);
		
		raf.seek(pos);
		
		int hasRead = 0;
		
		byte[] buf = new byte[64];
		
		while((hasRead = raf.read(buf)) > 0){
			fos.write(buf,0,hasRead);
		}
		
		raf.seek(pos);
		raf.write(content.getBytes());
		
		while((hasRead = fis.read(buf)) > 0){
			raf.write(buf, 0, hasRead);
		}
	}
}
```