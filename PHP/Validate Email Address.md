 <?php 
 
 if (!filter_var($emailAddy, FILTER_VALIDATE_EMAIL)) {
    echo "Your email address is not valid."
  }

  ?>