Use the following for creating a WPDB instance.

    $db = new wpdb('databaseuser', 'databasepassword', 'databasename', 'host');

Use the following to turn on error reporting.

    $db->show_errors();
    $db->print_error();

To initiate a query use the format:

    $ourData = $db->query( $db->prepare(" SELECT * INTO tablename WHERE itemnumber = %d AND itemtext = %s )", array( $itemnumber, $itemtext )));

Use placeholders to represent information in the query. You can also use OBJECT, ARRAY_A (associative) and ARRAY_N (named) to return data. The array in the statement above will default to OBJECTS.

**Named Array

    $ourData = $db->query( $db->prepare(" SELECT * INTO tablename WHERE itemnumber = $itemnumber AND itemtext = $itemtext )", ARRAY_N));

**Associative Array

    $ourData = $db->query( $db->prepare(" SELECT * INTO tablename WHERE itemnumber = $itemnumber AND itemtext = $itemtext )", ARRAY_A));

**Object

    $ourData = $db->query( $db->prepare(" SELECT * INTO tablename WHERE itemnumber = $itemnumber AND itemtext = $itemtext )", OBJECT));