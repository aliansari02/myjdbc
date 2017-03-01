# myjdbc
Creating a JDBC


import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.Date;
import java.beans.Statement;

public class sample {

	public static void main(String[] args) throws ClassNotFoundException {
		// TODO Auto-generated method stub
		
		Class.forName("oracle.jdbc.driver.OracleDriver");

		 Connection dbConnection = null;
		 ResultSet rs = null;
		 
		 try{
			 dbConnection = DriverManager.getConnection(
					 "jdbc:oracle:thin:@localhost:1521:xe",
					 "system",
					 "pizza");
			 
		// Statement st = (Statement)conn.createStatement();
			 java.sql.Statement st = dbConnection.createStatement();
			
			 rs=  st.executeQuery("select * from emp");		
			 //ececuteQuery("select * from emp");
			 
			 while(rs.next()){
				 int EmpId = rs.getInt("emp_id");
				 String empName = rs.getString("emp_name");
				 Date dob = rs.getDate("dob");
				 //String pass = rs.getString("password");
				 System.out.println(EmpId + " - "+ empName + " - " + dob );
				 
			 }
		 
			 
			 
		 }
		 
			 
			 catch(SQLException e)
			 {
				 e.printStackTrace();
				 
				 
			 }
		 finally{
			 try{
				 rs.close();
				 dbConnection.close();
			 }
			 catch(SQLException e){
				 e.printStackTrace();
			 }
		 }
			 
			 
			 
		 
	}

}

