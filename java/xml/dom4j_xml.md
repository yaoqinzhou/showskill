#Dom4j操作xml

###创建xml
```
DocumentFactory factory = new DocumentFactory();
Document doc = factory.createDocument();

/*还可以以下静态方法创建
Document doc = DocumentHelper.createDocument();
		doc.setXMLEncoding("utf-8");
*/

Element root = doc.addElement("rootNodeName");

Element node1 = root.addElement("node1");
node1.setAttributeValue("name", "node1");
node1.setText("node1Text");

String str = doc.asXML();

System.out.println(str);
```

###解析xml
```
public static void readXmlStr(String xmlStr) throws Exception{
	Document doc = DocumentHelper.parseText(xmlStr);
	
	Element root = doc.getRootElement();
	
	String rootName = root.getName(); 
	System.out.println("rootName = " + rootName);
	
	//遍历根节点下的所有子节点
	Iterator it = root.elementIterator();
	
	while(it.hasNext()){
		Element node = (Element)it.next();
		
		String text = node.getText();
		
		System.out.println("text = " + text);
	}
}
```
