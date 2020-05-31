jQuery( document ).ready(function($){
		var lenMarquee = $('.marquee-items div').length;
		var i = 1;
		var $marqueeItem;
		setInterval(function(){
			if(i > lenMarquee){
				i = 1;
			}
			$marqueeItem = ".marquee-item-" + i;
			if($($marqueeItem).css('display')=='none'){
				$($marqueeItem).fadeToggle(function(){
					setInterval(5000);
				});
			} else {
			$($marqueeItem).fadeToggle(function(){
				setInterval(5000);
			})
			i++;
		}
		},3000)
});