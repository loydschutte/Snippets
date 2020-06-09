<?php

// WP_Query arguments
$args = array (
    'post_type'              => array( 'bio' ),
    'post_status'            => array( 'published' ),
    'ignore_sticky_posts'    => false,
    'order'                  => 'ASC',
    'orderby'                => '_placement',
    'meta_key'               => '_placement',
);

// The Query
$query = new WP_Query( $args );

// The Loop
if ( $query->have_posts() ) { ?>

    <div class="container">
        <div class="row">
            <?php while ( $query->have_posts() ) { ?>
                <div class="col-lg-12">
                    <?php $query->the_post();?>
                    
                    <h3><?php the_title(); ?></h3>
                    <div><?php the_content(); ?></div>
                    
                </div><!-- .col-lg-12 -->
            <?php } ?>
        </div><!-- .row -->
    </div><!--. container -->

<?php } 
wp_reset_postdata();
?>

