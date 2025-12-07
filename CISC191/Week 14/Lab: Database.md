# Activity: Manipulating databases using Java

## Objective

Write a code to access and manipulate databases using MySQL J connector

## Task
Assignment Code:
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class DatabaseLab {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/Miramar";
        String user = "testuser";
        String password = "testpass";

        Connection conn = null;

        try {
            conn = DriverManager.getConnection(url, user, password);
            System.out.println("Connected to MySQL!");

            String insertSQL = """
                INSERT INTO Student 
                (ssn, firstName, mi, lastName, birthDate, street, phone, zipCode, deptId)
                VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)
                """;

            PreparedStatement insertStmt = conn.prepareStatement(insertSQL);
            insertStmt.setString(1, "111222333");
            insertStmt.setString(2, "Philip");
            insertStmt.setString(3, "D");  // Middle initial (table only allows 1 char)
            insertStmt.setString(4, "Collins");
            insertStmt.setString(5, "1951-01-30");
            insertStmt.setString(6, "NA");
            insertStmt.setString(7, "NA");
            insertStmt.setString(8, "NA");
            insertStmt.setString(9, "1234");
            insertStmt.executeUpdate();

            System.out.println("Record inserted.");

            String updateSQL = "UPDATE Student SET zipCode = ? WHERE ssn = ?";
            PreparedStatement updateStmt = conn.prepareStatement(updateSQL);
            updateStmt.setString(1, "92126");
            updateStmt.setString(2, "111222333");
            updateStmt.executeUpdate();

            System.out.println("Zip code updated.");

        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            try {
                if (conn != null && !conn.isClosed()) {
                    conn.close();
                    System.out.println("Connection closed.");
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}

```
## This is my flowchart:
<img width="121" height="761" alt="DatabaseLab drawio" src="https://github.com/user-attachments/assets/d6ca4f7f-5167-4654-807d-f3fe58d1c9fe" />

## Challenges encountered while performing the lab:
The most difficult part of this assignment for me was installing MySQL and getting MySQL to connect to IntelliJ.
