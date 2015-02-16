#ArrayList和LinkedList如何选择

ArrayList数组实现，LinkedList链表实现

当遇到访问比插入和删除频繁的时候，应该用ArrayList,反之应该用LinkedList.

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
当向ArrayList中新增数据的时候，java会去检查是否有足够的空间存储对象，没有就新建一个长度更长的数组，然后
调用Array.copyOf将之前的数组复制过去，现有的数组引用指向新的数组。




