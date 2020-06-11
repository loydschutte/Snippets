Send data via $_POST to a page using CURL.

Option 1: Use http_build_query to encode an already existing aray to pass data.

    $postdata =  array(
        "recipients" => array(2094063904),
        "message" => "Test",
        "key" => "iO7JPa3bOHd6nEJ5Db7ivKVwbefhFcO1"
    );

    $ch = curl_init();    
    curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postdata));
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);  
    curl_setopt($ch, CURLOPT_URL, "https://sjcourts.org/message/index_test.php");
    $response = curl_exec($ch);


    echo print_r($response, true);

Option 2: Build the POST string and manually encode objects from an array.

    $url = 'http://domain.com/get-post.php';
    $fields = array(
        'lname' => 'John',
        'fname' => 'Doe'
    );

    //url-ify the data for the POST
    foreach($fields as $key=>$value) { $fields_string .= $key.'='.$value.'&'; }
    rtrim($fields_string, '&');

    //open connection
    $ch = curl_init();

    //set the url, number of POST vars, POST data
    curl_setopt($ch,CURLOPT_URL, $url);
    curl_setopt($ch,CURLOPT_POST, count($fields));
    curl_setopt($ch,CURLOPT_POSTFIELDS, $fields_string);

    //execute post
    $result = curl_exec($ch);

    //close connection
    curl_close($ch);