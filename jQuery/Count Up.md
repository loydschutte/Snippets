<div class="count" data-count="475">0</div>

$('.count').each(function() {
        var $this = $(this),
            countTo = $this.attr('data-count');
            console.log(countTo);
        
        $({ countNum: $this.text()}).animate({
            countNum: countTo
        },

        {   duration: 5000,
            easing:'linear',
            step: function() {
            $this.text(Math.floor(this.countNum));
            console.log('counting');
            },
            complete: function() {
            $this.text(this.countNum);
            console.log('finished');
            }
        });  
    });