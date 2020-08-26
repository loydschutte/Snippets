Create a thumbnail from a pdf using imagemagick.

    $filename = 'converted.png';
    $pdflocation = $pdflocation . '[0]';
    $im = new imagick($pdflocation);
    $im->setImageBackgroundColor('#ffffff');
    $im->setImageAlphaChannel(imagick::ALPHACHANNEL_REMOVE);
    $im = $im->mergeImageLayers(imagick::LAYERMETHOD_FLATTEN);

    $im->setImageFormat("png32");
    $im->writeImage($filename);
    
    header('Content-Type: image/png');
    echo $im;