#jdbc连接例子

```
public class TestJdbc {
	
	public static void main(String[] args){
		
		Connection conn = null;
		Statement stmt = null;
		ResultSet rs = null;
		
		try{
			Class.forName("oracle.jdbc.driver.OracleDriver");
			
			String url = "jdbc:oracle:thin:@127.0.0.1:1521:orac10g";
			String userName = "xxx";
			String pwd = "xxx";
			
			conn = DriverManager.getConnection(url, userName, pwd);
			stmt = conn.createStatement();
			
			rs = stmt.executeQuery("select sysdate from dual");
			
			while(rs.next()){
				String sysdate = rs.getString("SYSDATE");
				
				System.out.println("sysdate = " + sysdate);
			}
			
		}catch(Exception ex){
			ex.printStackTrace();
		}finally{
			try{
				rs.close();
				stmt.close();
				conn.close();
			}catch(Exception ex){
				ex.printStackTrace();
			}
		}
	}
}
```