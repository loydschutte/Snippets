# Add a Dynamic Sidebar to a Page Template

This snippet will add a dynamic sidebar/widget area to your page if there is content within the sidebar.

```
<?php if ( is_active_sidebar( 'sidebar-name-from-functions.php' ) ) : ?>
		<?php dynamic_sidebar( 'sidebar-name-from-functions.php' ); ?>
<?php endif; ?>
```