<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "bestforless";

// Connect to the database
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);
}

// Fetch data
$sql = "SELECT * FROM users";
$result = $conn->query($sql);
?>

<!DOCTYPE html>
<html>
<head>
  <title>Admin Page - View Profiles</title>
  <style>
    table {
      border-collapse: collapse;
      width: 80%;
      margin: auto;
    }
    th, td {
      padding: 10px;
      border: 1px solid #aaa;
      text-align: left;
    }
    th {
      background-color: #f4f4f4;
    }
    h2 {
      text-align: center;
    }
  </style>
</head>
<body>
  <h2>Saved Profiles</h2>

  <table>
    <tr>
      <th>ID</th>
      <th>Full Name</th>
      <th>Date of Birth</th>
      <th>Contact Info</th>
      <th>Country/Region</th>
      <th>City</th>
    </tr>

    <?php if ($result->num_rows > 0): ?>
      <?php while($row = $result->fetch_assoc()): ?>
        <tr>
          <td><?= $row['id'] ?></td>
          <td><?= $row['full_name'] ?></td>
          <td><?= $row['date_of_birth'] ?></td>
          <td><?= $row['contact_info'] ?></td>
          <td><?= $row['country_region'] ?></td>
          <td><?= $row['city'] ?></td>
        </tr>
      <?php endwhile; ?>
    <?php else: ?>
      <tr><td colspan="6">No data found.</td></tr>
    <?php endif; ?>

  </table>

</body>
</html>

<?php
$conn->close();
?>
