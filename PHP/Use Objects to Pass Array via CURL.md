 Mix objects and arrays to pass data via CURL and PHP
 
    $data =  [
        "array1" => array(
            'array1a' => $arrayvalue1,
            'array2a' => $arrayvalue2,
            'array3a' => $arrayvalue3
        ),
        "item1" => $value1,
        "item2" => $value2,
        ];
    
    $ch = curl_init();    
        curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
        curl_setopt($ch, CURLOPT_POST, true);
        curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);  
        curl_setopt($ch, CURLOPT_URL, "https://sjcourts.org/message/index_test.php");
        $response = curl_exec($ch);
        echo "Sent text...<br/>";