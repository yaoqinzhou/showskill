#基于AspectJ配置切面示例

```
@Aspect  //标识这是一个切面
public class AspectService {
	//定义切点
	//这里以com.test包下，类中以aop_开始的方法做为切点
	@Pointcut("execution(* com.test..*.aop_*(..))") 
	public void aspect(){}
	
	//定义增强类型
	@Around("aspect()")
	public void around(JoinPoint joinPoint){
		//joinpoint就是连接点
		
		//before do something
		
		//执行连接点的方法
		((ProceedingJoinPoint) joinPoint).proceed();
		
		//after do something
	}

}
```
