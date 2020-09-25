Handy little function to succinctly write to a MySQL database using MySQLi Prepared Statements.

    function prepared_query($mysqli, $sql, $params, $types = "")
        {
            $types = $types ?: str_repeat("s", count($params));
            $stmt = $mysqli->prepare($sql);
            $stmt->bind_param($types, ...$params);
            $stmt->execute();
            return $stmt;
        }
    
    $link = "your connection credentials";

    $sql = "INSERT INTO `ourtable` (
        `column1`, `column2`,`column3`
            )
        values
            (?,?,?)";

        $stmt = prepared_query($link,$sql,[$column1value,$column2value, $column3value]);

        mysqli_stmt_store_result ( $stmt );