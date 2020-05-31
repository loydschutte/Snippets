$('.expandable').click(function(){
        var target = $(this).data('target');
        if(target != ''){
            target = '.'+target;
            $(target).slideToggle('slow');
            $(this).ready(function($){
                $('.expanded, .contracted').toggle();
            }) 
        } 
    })