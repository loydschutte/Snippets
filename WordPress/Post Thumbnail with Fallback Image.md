<?php if (has_post_thumbnail()) {
						the_post_thumbnail('original', array( 'class'	=> "img-responsive"));
					} else { ?>
						<img src="<?php echo get_template_directory_uri(); ?>/img/header-image-bus.jpg" class="img-header" alt="img-header">
					<?php } ?>