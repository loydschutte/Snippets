<?php

function display_initiatives(){
    	$args = array( 'post_type' => 'initiatives'	
		);
	$loop = new WP_Query( $args );
		while ( $loop->have_posts() ) : $loop->the_post(); 
		$post = get_post( $post );
		$title = isset( $post->post_title ) ? $post->post_title : '';
		$permalink = '<a href="' .esc_url( get_permalink() ) . '">';
		$filler .= '<div class="initiative-title">';
		$filler .= $permalink;
		$filler .= $title;
		$filler .= '</a></div>';  
		echo $filler;
		endwhile; 

		wp_reset_query();
	return $filler;
}

add_shortcode( 'initiatives', 'display_initiatives' );

?>