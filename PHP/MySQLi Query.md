Basic MySQLi query that doesn't use prepared statements.

$link = mysqli_connect($location, $user, $pass, $database);
$query = "SELECT * FROM database.table WHERE ourcondition = true";
$result = mysqli_query($link, $query);
$rows = mysqli_fetch_array($result);
$ouritem = $rows['name'];
or

$rows = mysqli_fetch_object($result);
$ouritem = $rows->name;