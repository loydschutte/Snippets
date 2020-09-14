Create a simple wrapper that waits until the dom has completely loaded before firing your javascript.

This replaces $('document').ready() in jQuery.    
 
    document.addEventListener('DOMContentLoaded', () => {
       
        // code
    
    })