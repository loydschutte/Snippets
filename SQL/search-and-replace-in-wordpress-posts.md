# Search and Replace in WordPress Posts

```
UPDATE wp_posts SET guid = REPLACE (guid, 'itemtofind', 'replacedwith');
UPDATE wp_posts SET post_content = REPLACE (post_content, 'itemtofind', 'replacedwith');
UPDATE wp_postmeta SET meta_value = REPLACE (meta_value, 'itemtofind','replacedwith');
```