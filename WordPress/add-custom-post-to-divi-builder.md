# Add Custom Post Type to Divi Builder

```
function my_et_builder_post_types( $post_types ) {
    $post_types[] = 'YOUR_CPT_HERE';
    $post_types[] = 'ANOTHER_CPT_HERE';
     
    return $post_types;
}
add_filter( 'et_builder_post_types', 'my_et_builder_post_types' );
```