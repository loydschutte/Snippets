<?php

function my_admin_help($text, $screen) {
	// Check we're only on my Settings page
	if (strcmp($screen, MY_PAGEHOOK) == 0 ) {

		$text = 'Here is some very useful information to help you use this plugin...';
		return $text;
	}
	// Let the default WP Dashboard help stuff through on other Admin pages
	return $text;
}

add_action( 'contextual_help', 'my_admin_help' );

?>