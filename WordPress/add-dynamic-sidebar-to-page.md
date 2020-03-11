# Add a Dynamic Sidebar to a Page Template

This snippet will add a dynamic sidebar/widget area to your page if there is content within the sidebar.

```
<?php if ( is_active_sidebar( 'sidebar-name-from-functions.php' ) ) : ?>
		<?php dynamic_sidebar( 'sidebar-name-from-functions.php' ); ?>
<?php endif; ?>
```

Alternatively you can wrap the sidebar in custom HTML.

```
<?php if ( is_active_sidebar( 'home_right_1' ) ) : ?>
	<div id="primary-sidebar" class="primary-sidebar widget-area" role="complementary">
		<?php dynamic_sidebar( 'home_right_1' ); ?>
	</div><!-- #primary-sidebar -->
<?php endif; ?>
```