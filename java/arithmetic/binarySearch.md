#二分法

###用二分法查询的数组一定是有序的，方法中在用递归实现
public static int binarySearch(int[] a,int from,int to,int key) throws Exception{
	if(from >= to){
		throw new Exception("invalid form index");
	}

	if(from < to){
		int middle = (from + to) >>> 1;
		
		int temp = a[middle];
		
		if(temp == key){
			return middle;
		}else if(temp > key){
			to = middle - 1;
		}else if(temp < key){
			from = middle + 1;
		}
	}

	return binarySearch(a,from,to,key);
}