<?php

function projects() {

	$labels = array(
		'name'                => _x( 'Projects', 'Post Type General Name', 'text_domain' ),
		'singular_name'       => _x( 'projects', 'Post Type Singular Name', 'text_domain' ),
		'menu_name'           => __( 'Projects', 'text_domain' ),
		'parent_item_colon'   => __( 'Projects:', 'text_domain' ),
		'all_items'           => __( 'All projects', 'text_domain' ),
		'view_item'           => __( 'View projects', 'text_domain' ),
		'add_new_item'        => __( 'Add new project', 'text_domain' ),
		'add_new'             => __( 'New project', 'text_domain' ),
		'edit_item'           => __( 'Edit projects', 'text_domain' ),
		'update_item'         => __( 'Update projects', 'text_domain' ),
		'search_items'        => __( 'Search projects', 'text_domain' ),
		'not_found'           => __( 'No projects found', 'text_domain' ),
		'not_found_in_trash'  => __( 'No projects found in Trash', 'text_domain' ),
	);
	$args = array(
		'label'               => __( 'projects', 'text_domain' ),
		'description'         => __( 'Projects', 'text_domain' ),
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
	register_post_type( 'projects', $args );

}

// Hook into the 'init' action
add_action( 'init', 'projects', 0 );

/** Add meta boxes if needed */

function add_project_meta_box(){
	add_meta_box('project_meta_box', 'Additional Project Details', 'project_meta_box', 'projects', 'side', 'low');
} add_action('add_meta_boxes','add_project_meta_box');

function project_meta_box(){
	global $post;
	echo '<input type="hidden" name="project_meta_noncename" id="project_meta_noncename" value="' . wp_create_nonce(plugin_basename(__FILE__)) . '" />';
	$varLink = get_post_meta($post->ID, "_link", true);
	$varSchool = get_post_meta($post->ID, "_school", true);
	$varHome = get_post_meta($post->ID, "_home", true);

	?>
	<label for="_position">	Link:
		<input type="text" name="_position" placeholder="Link" value="<?php echo $varLink; ?>" class="widefat" />
	</label>
	<hr>
	<label for="_cell"> School:
	<input type="text" name="_cell" placeholder="School" value="<?php echo $varSchool; ?>" class="widefat" />
	</label>
	<hr>
	<label for="_email"> Home:
	<input type="text" name="_email" placeholder="Home" value="<?php echo $varHome; ?>" class="widefat" />
	</label>
<?php
}
function cp_save_projectboxes($post_id, $post){

	if (!wp_verify_nonce($_POST["mass_meta_noncename"], plugin_basename(__FILE__))) {
		return $post->ID;
	}

	if (!current_user_can("edit_post", $post->ID)){
		return $post_id;
	}
	
	$project_meta["_link"] = $_POST['_link'];
	$project_meta["_school"] = $_POST['_school'];
	$project_meta["_home"] = $_POST['_home'];
	
	
	foreach ($project_meta as $key => $value){
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
add_action("save_post", "cp_save_projectboxes", 1, 2);

?>