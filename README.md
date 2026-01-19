import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class Main {
    public static void main(String[] args) {

        String url = "jdbc:mysql://localhost:3306/quiz_db"
                + "?useSSL=false"
                + "&serverTimezone=UTC"
                + "&allowPublicKeyRetrieval=true";

        String user = "root";
        String password = "apurbaict";

        String sql = "INSERT INTO questions(question, option1, option2, option3, option4, correct_answer) "
                   + "VALUES (?, ?, ?, ?, ?, ?)";

        try (Connection con = DriverManager.getConnection(url, user, password);
             PreparedStatement pst = con.prepareStatement(sql)) {

            pst.setString(1, "What is Java?");
            pst.setString(2, "Language");
            pst.setString(3, "OS");
            pst.setString(4, "Browser");
            pst.setString(5, "Device");
            pst.setString(6, "Language");

            int row = pst.executeUpdate();

            if (row > 0) {
                System.out.println("✅ Data Inserted Successfully!");
            }

        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}

