$(document).ready(function(){
$('span,p,div').attr('unselectable', 'on')
         .css('user-select', 'none')
         .on('selectstart', false);
});