<?php

In Function.php:

/**
 * Custom Post Type: Logo Grid Section
 */


function logo_grid() {

    $labels = array(
        'name'                => _x( 'Logo Grid', 'Post Type General Name', 'text_domain' ),
        'singular_name'       => _x( 'logo_grid', 'Post Type Singular Name', 'text_domain' ),
        'menu_name'           => __( 'Logo Grid', 'text_domain' ),
        'parent_item_colon'   => __( 'Logo Grid:', 'text_domain' ),
        'all_items'           => __( 'All Logo Grid items', 'text_domain' ),
        'view_item'           => __( 'View Logo Grid item', 'text_domain' ),
        'add_new_item'        => __( 'Add New Logo Grid item', 'text_domain' ),
        'add_new'             => __( 'New Logo Grid items', 'text_domain' ),
        'edit_item'           => __( 'Edit Logo Grid items', 'text_domain' ),
        'update_item'         => __( 'Update Logo Grid items', 'text_domain' ),
        'search_items'        => __( 'Search Logo Grid items', 'text_domain' ),
        'not_found'           => __( 'No Logo Grid item found', 'text_domain' ),
        'not_found_in_trash'  => __( 'No Logo Grid items found in trash', 'text_domain' ),
    );
    $args = array(
        'label'               => __( 'Logo Grid', 'text_domain' ),
        'description'         => __( 'Logo Grid', 'text_domain' ),
        'labels'              => $labels,
        'supports'            => array( 'title', 'editor', 'thumbnail' ),
        'hierarchical'        => false,
        'public'              => true,
        'show_ui'             => true,
        'show_in_menu'        => true,
        'show_in_nav_menus'   => true,
        'show_in_admin_bar'   => true,
        'menu_position'       => 20,
        'menu_icon'           => 'dashicons-admin-home',
        'can_export'          => true,
        'has_archive'         => true,
        'exclude_from_search' => true,
        'publicly_queryable'  => true,
        'capability_type'     => 'page',
    );
    register_post_type( 'logo_grid', $args );

}

// Hook into the 'init' action
add_action( 'init', 'logo_grid', 0 );

/** Add meta boxes if needed */

function add_logo_grid_box(){
    add_meta_box('logo_grid_box', 'Logo Grid', 'logo_grid_box', 'logo_grid', 'side', 'low');
} add_action('add_meta_boxes','add_logo_grid_box');

function logo_grid_box(){
    global $post;
    echo '<input type="hidden" name="logo_grid_noncename" id="logo_grid_noncename" value="' . wp_create_nonce(plugin_basename(__FILE__)) . '" />';

    $varOrder = get_post_meta($post->ID, "_order", true);
    ?>

    <label for="order">
        <input name="_order" id="order" type="text" value="<?php echo $varOrder; ?>">
    </label>
    <?php
}
function cp_save_logoboxes($post_id, $post){

    if (!wp_verify_nonce($_POST["logo_grid_noncename"], plugin_basename(__FILE__))) {
        return $post->ID;
    }

    if (!current_user_can("edit_post", $post->ID)){
        return $post_id;
    }

    $logo_grid["_order"] = $_POST["_order"];


    foreach ($logo_grid as $key => $value){
        if($post->post_type == "revision") return;
        $value = implode(",", (array)$value);
        if (get_post_meta($post->ID, $key, false)){
            update_post_meta($post->ID, $key, $value);
        } else {
            add_post_meta($post->ID, $key, $value);
        }
        if (!$value) delete_post_meta_by_key($post->ID, $key);
    }

}
add_action("save_post", "cp_save_logoboxes", 1, 2);


In page.php or on template:

<section class="logo-grid">
<?php $args = array (
    'post_type'              => array( 'logo_grid' ),
    'post_status'            => array( 'published' ),
    'ignore_sticky_posts'    => false,
    'order'                  => 'ASC',
    'orderby'                => '_order',
    'meta_key'               => '_order',
);

// The Query
$query = new WP_Query( $args );

// The Loop
if ( $query->have_posts() ) { ?>

    <div class="container">
        <div class="row">
			<div class="col-lg-12">
				<div class="flex-container">
            <?php while ( $query->have_posts() ) { ?>
                
                    <?php $query->the_post();?>
                    <div class="flex-item">
						<?php the_post_thumbnail('post-thumbnail', array( 'class'	=> "img-responsive")); ?>	
					</div><!-- .flex-item -->
				<?php } ?>			
					</div><!-- .flex-container -->
                </div><!-- .col-lg-12 -->
            
        </div><!-- .row -->
    </div><!--. container -->

<?php } 
wp_reset_postdata();
?>
</section>

In SCSS file:

.logo-grid {
    padding: 60px 0px;
    
    .flex-container {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: space-evenly;
        align-items: center;
        align-content: space-between;

        .flex-item {
            width: auto;
            height: 70px;
            text-align: center;
            padding: 0 1vw;

            img {
                max-height: 45px;
                width: auto;
            }
        }
    }
}

?>