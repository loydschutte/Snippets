<?php

add_action('admin_head', 'my_custom_logo');

function my_custom_logo() {
   echo '<style type="text/css">
         #header-logo { background-image: url('.get_bloginfo('template_directory').'/images/custom-logo.gif) !important; }</style>';
}

?>