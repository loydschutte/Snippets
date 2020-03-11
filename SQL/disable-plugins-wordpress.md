# Disable All Plugins in WordPress in the Database

```
UPDATE wp_options SET option_value = '' WHERE option_name = 'active_plugins';
```