#Cache Files

Tell the users computer to cache the files.

<FilesMatch ".(flv|gif|jpg|jpeg|png|ico|swf|js|css|pdf)$">

Header set Cache-Control "max-age=2592000"

</FilesMatch>