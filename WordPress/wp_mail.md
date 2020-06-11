Use the built in wp_mail() function to send email through WordPress.

    $to = $email;
    $subject = "Subject";
    $headers = array('From: noreply@yourdomain.com','Reply-to: noreply@yourdomain.com',' Content-Type: text/html; charset=UTF-8');
    $message = "This is where your message would go. It\'s an html email so you can use markup within the message for formatting.";

    $sent = wp_mail($to, $subject, $message, $headers);
    if($sent) {
        echo "The email has been sent";
    }
    else  {
        echo "<br/>";
        echo "Ooops! That didn't work.";
        error_log(print_r($wp_error, true));
        echo "<br/>";
        echo "to: " . $to . "<br/>";
        echo "subject: " . $subject . "<br/>";
        echo "headers: " . print_r($headers,true) . "<br/>";
        echo "message: " . $message . "<br/>";
        
    }