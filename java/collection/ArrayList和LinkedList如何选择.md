#ArrayList��LinkedList���ѡ��

ArrayList����ʵ�֣�LinkedList����ʵ��

##ArrayList�е�������ɾ��Ч�ʱȽϵ�

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
���Կ���������ɾ���������õ���Array.copyOf��System.arraycopy������Array.copyOf�л����System.arraycopy��




