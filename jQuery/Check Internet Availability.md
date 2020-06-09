$(document).ready(function() {
  function checkInternet() {
    var status = navigator.onLine;
    if (status)
      return true;
    else
      return false;
  }
   var bIsInternetAvailable = checkInternet(); 
});