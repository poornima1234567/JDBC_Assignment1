# JDBC_Assignment1

SQL Uppgift:1a
CREATE SCHEMA `sqlandjava` ;
CREATE TABLE `sqlandjava`.`people` (
  `person_id` INT(11) NOT NULL,
  `firstname` VARCHAR(45) NOT NULL,
  `lastname` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`person_id`));
INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('1', 'Anna', 'Bolt');
INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('2', 'Carl', 'Dolk');
INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('3', 'Erik', 'Fram');
INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('4', 'Gina', 'Hult');
CREATE USER user@localhost IDENTIFIED BY 'password'; 
GRANT SELECT ON jdbc_demo.people TO super@localhost;
SQL Uppgift:1b
package sqlandjava;

    import java.sql.Connection;
	import java.sql.DriverManager;
    import java.sql.ResultSet;

     import java.sql.Statement;

     public class Assignment1 {
	
		public static Connection getConnection() throws Exception {
			try {
				String url = "jdbc:mysql://localhost:3306/sqlandjava";
				String username = "user";
				String password = "password";
				
				Connection conn = DriverManager.getConnection(url,username,password);
				System.out.println("Connected to Database!");
				return conn;
			}catch(Exception e)
			{
				System.out.println(e);
			}
			return null;
		}

		public static void main(String[] args) throws Exception {
			// TODO Auto-generated method stub
	        Connection conn = getConnection();
	        Statement statment = conn.createStatement();
	        ResultSet res = statment.executeQuery("select*from people");
	        while(res.next()) {
	        	//System.out.println(res.getString("id"));
	        	System.out.println(res.getString("person_id")+ ":" + res.getString("firstname")+" "+ res.getString("lastname"));

	        
	        }
		}

	}

1:Anna Bolt
2:Carl Dolk
3:Erik Fram
4:Gina Hult

