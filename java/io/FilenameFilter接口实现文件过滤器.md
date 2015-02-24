#利用FilenameFilter接口实现文件过滤器

```
//用了command设计模式
public class TestFilter {

	public static void main(String[] args){
		MyFilenameFilter myFilenameFilter = new TestFilter().new MyFilenameFilter();
	
		File file = new File(".");
		String[] nameList = file.list(myFilenameFilter);
		
		for(String name : nameList){
			System.out.println("name = " + name);
		}
	}
	
	class MyFilenameFilter implements FilenameFilter{

		@Override
		public boolean accept(File dir, String name) {
			
			return name.endsWith(".java") || new File(name).isDirectory();
		}
		
	}
}
```