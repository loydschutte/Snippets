<?php

add_filter( 'login_headerurl', 'custom_loginlogo_url' );
function custom_loginlogo_url($url) {
    return '';
}
function my_login_logo() { ?>
    <style type="text/css">
        body {
            background: rgba(15, 116, 187, 1);
            color: rgba(255, 255, 255, 1);
        }

        body.login div#login h1 a {
            background-image: url(<?php echo get_stylesheet_directory_uri(); ?>/img/logo.svg);
            height: 80px;
            width: 220px;
        }

        .login h1 a {
            background-size: 100% !important;
            width: auto;
            height: auto;
        }
    </style>
<?php }
add_action( 'login_enqueue_scripts', 'my_login_logo' );

?>