<?php 
$varDBName = 'sampledb';
$varDBUser = 'demouser';
$varDBPass = 'demopass)';
$varLocation = 'localhost';

$link = mysqli_connect($varLocation, $varDBUser, $varDBPass, $varDBName);

if (!$link) {
    echo "ERROR: Unable to connect" . PHP_EOL;
    echo "DEBUGGING ERRNO: " . mysqli_connect_errno() . PHP_EOL;
    echo "DEBUGGGING ERROR: " . mysqli_connect_error() . PHP_EOL;
    exit;
} else {
    echo "<script> 
    console.log ('Connected!');
    </script>";
}