# Allow SVG graphics to be uploaded via the media uploader in WordPress

Add the following code to your functions.php file to allow SVG's to be uploaded via the built in media uploader in WordPress.

```
function cc_mime_types($mimes) {
  $mimes['svg'] = 'image/svg+xml';
  return $mimes;
}
add_filter('upload_mimes', 'cc_mime_types');
```