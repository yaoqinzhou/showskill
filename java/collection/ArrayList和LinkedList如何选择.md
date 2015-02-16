#ArrayList和LinkedList如何选择

ArrayList数组实现，LinkedList链表实现

##ArrayList中的新增和删除效率比较低

```
public boolean add(Object obj){
	ensureCapacity(size + 1);
	elementData[size++] = obj;
	return true;
}

public void ensureCapacity(int i){
	modCount++;
	int j = elementData.length;
	if(i > j)
	{
		Object aobj[] = elementData;
		int k = (j * 3) / 2 + 1;
		if(k < i)
			k = i;
		elementData = Arrays.copyOf(elementData, k);
	}
}

public Object remove(int i){
	RangeCheck(i);
	modCount++;
	Object obj = elementData[i];
	int j = size - i - 1;
	if(j > 0)
		System.arraycopy(((Object) (elementData)), i + 1, ((Object) (elementData)), i, j);
	elementData[--size] = null;
	return obj;
}
```
可以看到新增和删除操作中用到了Array.copyOf和System.arraycopy方法，Array.copyOf中会调用System.arraycopy。




