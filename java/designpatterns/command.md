##命令模式实现

该模式可以使调用方法和处理行为真正的分离

###command接口
public interface Command{
    void process(int[] target);
}

###两个不同的实现类
public class AddCommand implements Command{
	
	public void process(int[] target){
		//todo add 
	}
}

public class PrintCommand implements Command{
	
	public void process(int[] target){
		//todo print
	}
}

###处理类
public class ProcessArray(){

    public void process(int[] target,Command command){
		command.process(target);
	}
}

###调用方法

public static void main(String[] args){
	ProcessArray pa = new ProcessArray();
	
	int[] target = new Int[]{1,2,3,4,5};
	
	pa.process(target,new AddCommand());
	pa.process(target,new PrintCommand());