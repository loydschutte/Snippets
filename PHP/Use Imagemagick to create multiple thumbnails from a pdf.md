Use Imagemagic to thumbnails for eachpage of a multipage pdf. This defaults to a 150 dpi which is perfect for internet viewing. Please keep in mind that the higher your resolution, the longer it will take to render and the more cpu cycles it will use. Something to keep in mind if you have limited cpu cycles or you're charged for cpu cycles monthly.

    $imagepath = './test/testfile.pdf';
    $imgname = './test/testfile';
    $im = new imagick($imagepath);
    $pages = $im->getNumberImages();
    $imagick = new imagick();
    $resolution = 150;
    $imagick->setResolution($resolution, $resolution);
    $imagick->readImage($imagepath);
    $imagick->setImageFormat('jpg');
    foreach($imagick as $i=>$imagick) { $imagick->writeImage($imgname. " page ". ($i+1) ." of ".  $pages.".jpg"); }
    $imagick->clear();