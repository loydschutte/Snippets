HTML FORM

<form action="mail.php" method="post" enctype="multipart/form-data">
	<input name="sender_name" placeholder="Your Name..."/>
	<input name="sender_email" placeholder="Your email..."/>
	<textarea placeholder="Your Message..." name="sender_message">
        <div class="captcha_wrapper">
		<div class="g-recaptcha" data-sitekey="YOUR_KEY"></div>
	</div>
	<button type="submit" id="send_message">Send Message!</button>
</form>

SERVER SIDE SCRIPT

<?php
	$sender_name = stripslashes($_POST["sender_name"]);
	$sender_email = (!filter_var($_POST["sender_email"], FILTER_VALIDATE_EMAIL));
	$sender_message = stripslashes($_POST["sender_message"]);
	$response = $_POST["g-recaptcha-response"];
	$url = 'https://www.google.com/recaptcha/api/siteverify';
	$data = array(
		'secret' => 'YOUR_SECRET',
		'response' => $_POST["g-recaptcha-response"]
	);
	$options = array(
		'http' => array (
			'method' => 'POST',
			'content' => http_build_query($data)
		)
	);
	$context  = stream_context_create($options);
	$verify = file_get_contents($url, false, $context);
	$captcha_success=json_decode($verify);
	if ($captcha_success->success==false) {
		echo "<p>You are a bot! Go away!</p>";
	} else if ($captcha_success->success==true) {
		echo "<p>You are not not a bot!</p>";
	}

    ?>