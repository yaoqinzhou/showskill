###生成10个不相同的随机整数
```
public static void main(String[] args){
	int[] arr = new int[10];
	
	for(int i=0; i<10; i++){
		arr[i] = i;
	}
	
	Random random = new Random();
	
	int size = arr.length;
	
	for(int k=0; k<size; k++){
		int index = 0;
		
		if((size - 1)-k != 0){
			index = random.nextInt((size - 1)-k);
		}
		
		int temp = arr[index];
		
		arr[index] = arr[size - (k + 1)];
		
		arr[size - (k + 1)] = temp;
		
		System.out.println("temp = " + temp);
	}
}
```