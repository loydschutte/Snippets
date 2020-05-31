 <style>
        .loop-item {
            display: none;
        }

        .item-1 {
            display: block;
        }
</style>
    
<div class="loop-item item-1">
  Hello
</div>
<div class="loop-item item-2">
  World
</div>
    
<script>
        $(document).ready(function($){
            var $item;
            var $len = $('.loop-item').length + 1;
            var $i = 1;
            if($len<=1){
                break;
            }
            if($len>1){
                $i = 2;
            }
            setInterval(function(){
                $('.loop-item').css('display','none');
                    $item = ".item-" + $i;
                        $($item).fadeToggle();
                    $i++;
                    if( $i >= $len ){
                        console.log("Before Reset $i: " + $i);
                        $i = 1;
                        console.log("After Reset $i: " + $i);
                    };
            }, 5000);
        })    
    </script>