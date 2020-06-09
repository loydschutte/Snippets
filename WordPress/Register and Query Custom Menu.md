In functions.php:

	register_nav_menus( array(
		'primary' => esc_html__( 'Primary', 'psi' ),
		) );


In Theme:
<?php 
					$args = array(
						'theme_location' 	=> 'primary', 
						'menu_class' 		=> 'header-menu',
						'container'		=> false
						);
					wp_nav_menu( $args); ?>