Make sure you have Image Magick installed and active by checking your PHPINI or PHPINFO. This will save the image as a JPG with a white background. If you choose you can change it to PNG. Without the white background the background will be transparent and may make the image difficult to see in some instances.

    $imagename = "oldimagename";
    $imgname = '../output/page/' . $imagename . '-tm.jpg';
    $imagepath = $imagepath . '[0]';
    $im = new imagick($imagepath);
    $im->setImageBackgroundColor('#ffffff');
    $im->setImageAlphaChannel(imagick::ALPHACHANNEL_REMOVE);
    $im = $im->mergeImageLayers(imagick::LAYERMETHOD_FLATTEN);

    $im->setImageFormat("jpg");
    $im->writeImage($imgname);