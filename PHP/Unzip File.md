  Unzip zip files using php's native function for unzipping.
  
  $zip = new ZipArchive;
  
  $res = $zip->open('file.zip');
  
  if ($res === TRUE) {
  
    $zip->extractTo('/myzips/extract_path/');
    
    $zip->close();
    
    echo 'woot!';
    
  } else {
  
    echo 'doh!';
    
  }
