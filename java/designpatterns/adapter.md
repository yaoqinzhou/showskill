#适配器模式

主要将两个不相干的类组合在一起使用，利用了java中的继承和组合

###两个不同的类
```
public class Person {
	public void say(){
		System.out.println("i am person");
	}
}

public class Teacher {
	public void say(){
		System.out.println("i am a teacher");
	}
}
```

###组合后的Adapter类
```
public class TeacherAdapter extends Person{

	private Teacher teacher;
	
	public TeacherAdapter(Teacher teacher){
		this.teacher = teacher;
	}
	
	public void say(){
		super.say();
		teacher.say();
	}
	
	public static void main(String[] args){
		new TeacherAdapter(new Teacher()).say();
	}
}
```