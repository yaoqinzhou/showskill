#选择排序

排序的数组可以使无序的

基本思想：在要排序的一组数中，选出最小的一个数与第一个位置的数交换，
然后在剩下的数当中再找最小的与第二个位置的数交换，如此循环到倒数第二个数和最后一个数比较为止。


```
public static int[] choiceSort(int[] a) throws Exception{
	if(a == null || a.length < 0){
		throw new Exception("error");
	}
	
	for(int i=0; i<a.length; i++){
		//假设当前下标定义为最小值下标
		int min = i;
		
		for(int j=i+1; j<a.length; j++){
			//如果有小于当前最小值的关键字
			if(a[min] > a[j]){
				//将此关键字的下标赋值给min
				min = j;
			}
		}
		
		//若min不等于i，说明找到最小值，交换
		if(min != i){
			int temp = a[i];
			a[i] = a[min];
			a[min] = temp;
		}
	}
	
	return a;
}
```