function display_initiatives($atts){
	extract( shortcode_atts( array(
        'limit' => 1,
		    ), $atts ) );

		if($limit == 0){
			$args = array( 'post_type' => 'initiatives',
			'order'                  => 'ASC',
			);
		} else {
			$args = array( 'post_type' => 'initiatives',
						'posts_per_page'         =>  $limit,
						'order'                  => 'ASC'
		);
		}
	$loop = new WP_Query( $args );
		while ( $loop->have_posts() ) : $loop->the_post();
		$post="";
		
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