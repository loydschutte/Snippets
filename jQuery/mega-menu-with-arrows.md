# Mega Drop Down Menu with Indicator Arrows

```
jQuery(document).ready(function($) {

        $('.expandable').addClass('menu-down');

        $('.expandable').click(function(e){
            e.preventDefault();
            $('.mega').css('display','none');
            var $title = $(this).find('a').attr('title');
            var $menulink = '.' + $title +'-menu';
            var check = $(this).hasClass('menu-down');
            
            $('.expandable').removeClass('menu-up');
            $('.expandable').addClass('menu-down');
            if(check){
                $(this).addClass('menu-up');
                $(this).removeClass('menu-down');
                $($menulink).fadeToggle();
            }
        })
    })

```