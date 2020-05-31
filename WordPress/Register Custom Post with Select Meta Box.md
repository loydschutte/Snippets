<?php

function home_meta() {

    $labels = array(
        'name'                => _x( 'Home Meta', 'Post Type General Name', 'text_domain' ),
        'singular_name'       => _x( 'home_meta', 'Post Type Singular Name', 'text_domain' ),
        'menu_name'           => __( 'Home Content Areas', 'text_domain' ),
        'parent_item_colon'   => __( 'Home Areas:', 'text_domain' ),
        'all_items'           => __( 'All Home Areas', 'text_domain' ),
        'view_item'           => __( 'View Home Area', 'text_domain' ),
        'add_new_item'        => __( 'Add New Home Area', 'text_domain' ),
        'add_new'             => __( 'New Home area', 'text_domain' ),
        'edit_item'           => __( 'Edit Home Area', 'text_domain' ),
        'update_item'         => __( 'Update Home Area', 'text_domain' ),
        'search_items'        => __( 'Search Home Area', 'text_domain' ),
        'not_found'           => __( 'No Home Area found', 'text_domain' ),
        'not_found_in_trash'  => __( 'No Home Area found in Trash', 'text_domain' ),
    );
    $args = array(
        'label'               => __( 'Home Areas', 'text_domain' ),
        'description'         => __( 'Home Areas', 'text_domain' ),
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
    register_post_type( 'home_meta', $args );

}

// Hook into the 'init' action
add_action( 'init', 'home_meta', 0 );

/** Add meta boxes if needed */

function add_home_meta_box(){
    add_meta_box('home_meta_box', 'Home Content Area Placement', 'home_meta_box', 'home_meta', 'side', 'low');
} add_action('add_meta_boxes','add_home_meta_box');

function home_meta_box(){
    global $post;
    echo '<input type="hidden" name="home_meta_noncename" id="home_meta_noncename" value="' . wp_create_nonce(plugin_basename(__FILE__)) . '" />';

    $varPlacement = get_post_meta($post->ID, "_placement", true);
    $values = get_post_custom( $post->ID );
    $selected = isset( $values['_placement'] ) ? esc_attr( $values['_placement'][0] ) : '';


    ?>

    <label for="placement">
        <select name="_placement" id="placement">
            <option value="left"  <?php selected( $selected, 'left' ); ?>>Left</option>
            <option value="right" <?php selected( $selected, 'right' ); ?>>Right</option>
        </select>
    </label>
    <?php
}
function cp_save_homeboxes($post_id, $post){

    if (!wp_verify_nonce($_POST["home_meta_noncename"], plugin_basename(__FILE__))) {
        return $post->ID;
    }

    if (!current_user_can("edit_post", $post->ID)){
        return $post_id;
    }

    $home_meta["_placement"] = $_POST["_placement"];


    foreach ($home_meta as $key => $value){
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
add_action("save_post", "cp_save_homeboxes", 1, 2);

?>