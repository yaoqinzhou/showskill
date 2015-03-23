###利用LinkedHashMap实现简单的缓存， 必须实现removeEldestEntry方法

```
public class LRULinkedHashMap<K,V> extends LinkedHashMap<K,V>{

	private final int maxCapacity;
	private static final float DEFAULT_LOAD_FACTOR = 0.75F;
	
	public LRULinkedHashMap(int maxCapacity){
		super(maxCapacity,DEFAULT_LOAD_FACTOR,true);
		this.maxCapacity = maxCapacity;
	}
	
	protected boolean removeEldestEntry(Map.Entry<K, V> eldest){
		return size() > maxCapacity;
	}
	
	public synchronized int size(){
		return super.size();
	}
	
	public synchronized V get(Object key){
		return super.get(key);
	}
	
	public synchronized V put(K key,V value){
		return super.put(key, value);
	}
	
	public synchronized void clear(){
		super.clear();
	}
	
    public synchronized Collection<Map.Entry<K, V>> getAll() {
        return new ArrayList<Map.Entry<K, V>>(super.entrySet());
    }
    //时间复杂度O(1)
    public synchronized boolean containsKey(Object key){
    	return super.containsKey(key);
    }
    //时间复杂度O(n)
    public synchronized boolean containsValue(Object value){
    	return super.containsValue(value);
    }
}
```