Iterate through the values of the POST array.

   foreach($_POST as $key => $val) {

        echo 'Field name : '.$key .', Value : '.$val.'<br>';
        $data[$key] = $val;
        
    }