#sleep和yield的区别

（1）sleep方法暂停后会给其他线程执行的机会，而不会考虑优先级。
     yield方法会给优先级相同或者大于的线程执行机会。
	 
（2）sleep方法会使线程转入阻塞状态，yield方法则会使线程进入就绪状态。

（3）sleep方法会抛出InterruptedException异常，而yield不会抛出任何异常。

（4）sleep比yield有更好的移植性，不建议使用yield方法来控制并发线程的执行。