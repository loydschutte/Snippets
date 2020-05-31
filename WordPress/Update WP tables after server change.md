UPDATE wp_posts SET guid = REPLACE (guid, 'old_server_address', 'new_server_address');
UPDATE wp_posts SET post_content = REPLACE (post_content, 'old_server_address', 'new_server_address');
UPDATE wp_postmeta SET meta_value = REPLACE (meta_value, 'old_server_address','new_server_address');