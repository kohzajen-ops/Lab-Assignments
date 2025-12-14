## Task
Assignment Code:

TestMySQLConnection.java:

```java
import java.sql.Connection;
import java.sql.DriverManager;

public class TestMySQLConnection {
    public static void main(String[] args) {
        try {
            Connection conn = DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/Auto",
                    "root",
                    "03032000"
            );
            System.out.println("✅ Connected to MySQL successfully!");
            conn.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

ProjectDatabaseInsert.java:

```java
import java.io.*;
import java.sql.*;

public class ProjectDatabaseInsert {

    private static String clean(String s) {
        return s.replace("\"", "").trim();
    }

    private static boolean isMissing(String s) {
        return s.equals("?") || s.equalsIgnoreCase("NA");
    }

    private static Float parseFloatSafe(String s) {
        s = clean(s);
        if (isMissing(s)) return null;
        return Float.parseFloat(s);
    }

    public static void main(String[] args) {

        String url = "jdbc:mysql://localhost:3306/Auto";
        String user = "root";
        String password = "03032000";

        String sql = "INSERT INTO Auto VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)";

        try (
                Connection conn = DriverManager.getConnection(url, user, password);
                PreparedStatement ps = conn.prepareStatement(sql);
                BufferedReader br = new BufferedReader(
                        new FileReader("data/auto-mpg.data-original.tsv"))
        ) {

            String line;
            int inserted = 0;

            while ((line = br.readLine()) != null) {

                String[] d = line.trim().split("\\t+");

                ps.setObject(1, parseFloatSafe(d[0]), Types.FLOAT);
                ps.setObject(2, parseFloatSafe(d[1]), Types.FLOAT);
                ps.setObject(3, parseFloatSafe(d[2]), Types.FLOAT);
                ps.setObject(4, parseFloatSafe(d[3]), Types.FLOAT);
                ps.setObject(5, parseFloatSafe(d[4]), Types.FLOAT);
                ps.setObject(6, parseFloatSafe(d[5]), Types.FLOAT);

                Float year = parseFloatSafe(d[6]);
                Float origin = parseFloatSafe(d[7]);

                ps.setObject(7, year == null ? null : year.intValue(), Types.INTEGER);
                ps.setObject(8, origin == null ? null : origin.intValue(), Types.INTEGER);

                ps.setString(9, clean(d[8]));

                ps.executeUpdate();
                inserted++;
            }

            System.out.println("Rows inserted: " + inserted);

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

ProjectDatabaseGUI.java:

```java
import javax.swing.*;
import java.sql.*;

public class ProjectDatabaseGUI {

    static final String URL = "jdbc:mysql://localhost:3306/Auto";
    static final String USER = "root";
    static final String PASS = "03032000";

    public static void main(String[] args) {

        JFrame frame = new JFrame("Auto MPG Database");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JTextField inputField = new JTextField(15);
        JButton searchButton = new JButton("Search");

        JTextArea outputArea = new JTextArea(15, 45);
        outputArea.setEditable(false);

        JSlider mpgSlider = new JSlider(0, 50, 20);
        mpgSlider.setMajorTickSpacing(10);
        mpgSlider.setPaintTicks(true);
        mpgSlider.setPaintLabels(true);

        JSlider hpSlider = new JSlider(0, 250, 100);
        hpSlider.setMajorTickSpacing(50);
        hpSlider.setPaintTicks(true);
        hpSlider.setPaintLabels(true);

        JButton filterButton = new JButton("Filter");

        JPanel topPanel = new JPanel();
        topPanel.add(new JLabel("Search (or ALL):"));
        topPanel.add(inputField);
        topPanel.add(searchButton);

        topPanel.add(new JLabel("Min MPG"));
        topPanel.add(mpgSlider);

        topPanel.add(new JLabel("Max HP"));
        topPanel.add(hpSlider);

        topPanel.add(filterButton);

        frame.add(topPanel, "North");
        frame.add(new JScrollPane(outputArea), "Center");

        searchButton.addActionListener(e -> {
            outputArea.setText("");
            String text = inputField.getText().trim();

            String sql = text.equalsIgnoreCase("ALL")
                    ? "SELECT * FROM Auto"
                    : "SELECT * FROM Auto WHERE car_name LIKE ?";

            try (
                    Connection conn = DriverManager.getConnection(URL, USER, PASS);
                    PreparedStatement ps = conn.prepareStatement(sql)
            ) {
                if (!text.equalsIgnoreCase("ALL")) {
                    ps.setString(1, "%" + text + "%");
                }

                ResultSet rs = ps.executeQuery();
                displayResults(rs, outputArea);

            } catch (Exception ex) {
                ex.printStackTrace();
            }
        });

        filterButton.addActionListener(e -> {
            outputArea.setText("");

            int minMpg = mpgSlider.getValue();
            int maxHp = hpSlider.getValue();

            String sql =
                    "SELECT * FROM Auto " +
                            "WHERE mpg >= ? " +
                            "AND (horsepower <= ? OR horsepower IS NULL)";

            try (
                    Connection conn = DriverManager.getConnection(URL, USER, PASS);
                    PreparedStatement ps = conn.prepareStatement(sql)
            ) {
                ps.setInt(1, minMpg);
                ps.setInt(2, maxHp);

                ResultSet rs = ps.executeQuery();
                displayResults(rs, outputArea);

            } catch (Exception ex) {
                ex.printStackTrace();
            }
        });

        frame.pack();
        frame.setLocationRelativeTo(null);
        frame.setVisible(true);
    }

    private static void displayResults(ResultSet rs, JTextArea output)
            throws SQLException {

        while (rs.next()) {
            output.append(
                    rs.getString("car_name") +
                            " | MPG: " + rs.getFloat("mpg") +
                            " | HP: " + rs.getInt("horsepower") +
                            "\n"
            );
        }
    }
}
```
