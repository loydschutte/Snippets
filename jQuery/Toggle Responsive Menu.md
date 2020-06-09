jQuery( document ).ready(function($){
		console.log('works ');
		jQuery('.menu-responsive-toggle, .menu-close').click( function(){
		jQuery('.menu-responsive').fadeToggle('slow');
		jQuery('.menu-responsive-toggle, .menu-close').fadeToggle();
		})
	});