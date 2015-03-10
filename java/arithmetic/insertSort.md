#插入排序

插入排序算法是一个对少量元素进行排序的有效算法。插入排序的工作原理与打牌时整理手中的牌的做法类似，
开始摸牌时，我们的左手是空的，接着一次从桌上摸起一张牌，并将它插入到左手的正确位置。为了找到这张牌的正确位置，
要将它与手中已有的牌从右到左进行比较，无论什么时候手中的牌都是排序好的。

从数组的第二个元素开始对比之前的元素

```
public static int[] insertSort(int[] a) throws Exception{
	if(a == null || a.length < 0){
		throw new Exception("error");
	}
	
	int i,key;
	
	//从数组的第二个元素开始
	for(int j = 1; j<a.length; j++){
		key = a[j];
		i = j -1;
		
		//a[i]比当前值大时，a[i]后移一位,空出i的位置，好让下一次循环的值后移 
		while(i >= 0 && a[i] > key){
			a[i+1] = a[i];
			i--;
		}
		//跳出循环(找到要插入的中间位置或已遍历到0下标)  
		a[i+1] = key;
	}

	return a;
}
```