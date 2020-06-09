<script>
var i = 0;
var images = [];
var time = 1000;

images[0] = 'http://placekitten.com/400/300';
images[1] = 'http://placepuppy.net/400/300';
images[2] = 'http://placekitten.com/400/300';
images[3] = 'http://www.placetrump.us/400/300';

function changeImg(){
    document.slide.src = images[i];

    if(i < images.length - 1){
        i++;
    } else {
        i = 0;
    }
    setTimeout("changeImg()", time);
    }

    window.onload = changeImg;
</script>
<img name="slide" width="400" height="300">