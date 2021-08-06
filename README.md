package javadb2;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class Javadb2 {

    public static void main(String[] args) {
         Connection con= null;
        try
        {
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Driver Loaded.");
        
        con=DriverManager.getConnection("jdbc:mysql://localhost:3306/acc_info","root","");
        System.out.println("Connection Established.");
        Statement st=con.createStatement();
       
        System.out.println("Table Contents");
        ResultSet rs=st.executeQuery("Select *from account");
           
        while(rs.next())
        {
            System.out.println(rs.getInt("acid")+" "+rs.getString("accname")+" a"+rs.getString("acctype")+" "+rs.getInt("accbal"));
        }

        con.close();
        }

        catch(ClassNotFoundException e)
        {
            System.out.println("Exception:"+e.getMessage());
        }
        catch(SQLException e)
        {
            System.out.println("SQLException:"+e.getMessage());
        }
  
    }
    
}
