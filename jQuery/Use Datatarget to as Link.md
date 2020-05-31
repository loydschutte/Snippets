jQuery(document).ready(function($){
		jQuery('button').click(function(){
			var target = jQuery(this).data('target');
			if(target != ''){
				window.location.href = '/'+target;
			} 
		})
	})