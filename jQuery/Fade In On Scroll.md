<div id="container">
    
    <div>Hello</div>
    <div>Hello</div>
    <div>Hello</div>
    <div>Hello</div>
    <div>Hello</div>
    <div>Hello</div>
    <div class="hideme">Fade In</div>
    <div class="hideme">Fade In</div>
    <div class="hideme">Fade In</div>
    <div class="hideme">Fade In</div>
    <div class="hideme">Fade In</div>
    
</div>

#container
{
    height:2000px;    
}

#container DIV
{ 
    margin:50px; 
    padding:50px; 
    background-color:lightgreen; 
}

.hideme
{
    opacity:0;
}

$(document).ready(function() {
    
    /* Every time the window is scrolled ... */
    $(window).scroll( function(){
    
        /* Check the location of each desired element */
        $('.hideme').each( function(i){
            
            var bottom_of_object = $(this).offset().top + $(this).outerHeight();
            var bottom_of_window = $(window).scrollTop() + $(window).height();
            
            /* If the object is completely visible in the window, fade it it */
            if( bottom_of_window > bottom_of_object ){
                
                $(this).animate({'opacity':'1'},500);
                    
            }
            
        }); 
    
    });
    
});