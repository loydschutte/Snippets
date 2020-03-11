# Create a Shortcode for Custom Post Type

Add this snippet to your functions.php file to create a shortcode used to query a custom post type named "testimonial".

```
function display_custom_post_type(){
    	$args = array( 'post_type' => 'testimonial',	
		);
	$loop = new WP_Query( $args );
		while ( $loop->have_posts() ) : $loop->the_post(); 
		$testimonial .= '<div class="project-thumbnail">' . the_post_thumbnail("post-thumbnail", array( "class" => "img-responsive")) . '</div>';
		$testimonial .= '<div class="section-head">'; // Style this to style your content
		$testimonial .= '<h3>' . the_title() . '</h3>';  // Style this to style your content
		$testimonial .= '</div>'; // Style this to style your content
		$testimonial .= '<div class="col-xs-12 col-md-12">' . the_content() . '</div>'; // Style this to style your content
		endwhile; 
		wp_reset_query();
        echo $testimonial;
	return $testimonial;
}

add_shortcode( 'nb-projects', 'display_custom_post_type' );
'''