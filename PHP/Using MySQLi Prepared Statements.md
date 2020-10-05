This is the php version (sans helper statements) to do prepared queries in MySQLi.
    
    mysqli_report(MYSQLI_REPORT_ERROR | MYSQLI_REPORT_STRICT);
    set_exception_handler(function($e) {
    error_log($e->getMessage());
    exit('Error connecting to database'); //Should be a message a typical user could understand
    });
    $mysqli = new mysqli("localhost", "username", "password", "databaseName");
    $mysqli->set_charset("utf8mb4");

    SELECT
    $stmt=$mysqli->prepare("SELECT * FROM mytable WHERE name=? AND age=?");
    $stmt->bind_param("si",$name,$age);
    $stmt->execute;
    $result=$stmt->get_result();
    while($row = $result->fetch_assoc()) {
        $address = $row['address'];
        $city = $row['city'];
        $zipcode = $row['zipcode'];
    }
    $stmt->close();

    INSERT
    $stmt = $mysqli->prepare("INSERT INTO myTable (name, age) VALUES (?, ?)");
    $stmt->bind_param("si", $name, $age);
    $stmt->execute();
    if($stmt->affected_rows === 0) exit('No rows affected');
    $stmt->close();

    UPDATE
    $stmt = $mysqli->prepare("UPDATE myTable SET name = ? WHERE id = ?");
    $stmt->bind_param("si", $name, $id);
    $stmt->execute();
    if($stmt->affected_rows === 0) exit('No rows affected');
    $stmt->close();

    DELETE
    $stmt = $mysqli->prepare("DELETE FROM myTable WHERE id = ?");
    $stmt->bind_param("i", $id);
    $stmt->execute();
    if($stmt->affected_rows === 0) exit('No rows affected');
    $stmt->close();

