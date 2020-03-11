# Change a tabs color on the sidebar on the WordPress Dashboard

Add this to your functions.php file to create custom css to chagne the color of a tab on the WordPress Dashboard.

```
function my_admin_colors() { ?>
    <style type="text/css">
       #menu-posts-callto {
            background: #C81C81 !important;
        }
        
        #menu-posts-logo_grid {
            background: #B91CC8 !important;
        }

        #menu-posts-industries {
            background: #631CC8 !important;
        }

    </style>
<?php }
add_action( 'admin_enqueue_scripts', 'my_admin_colors' );

```