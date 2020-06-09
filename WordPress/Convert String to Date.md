<?php

$vardate = $post->_date; //Date from database via POST
$ourdate = date("F j, Y", strtotime($vardate)); // Convert date to Month Day, Year.
echo $ourdate;

?>