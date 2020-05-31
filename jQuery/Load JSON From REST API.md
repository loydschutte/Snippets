jQuery(document).ready(function( $ ) {
    $.ajax( {
        type: 'GET',
        url: 'http://yourapiserver.com',
        dataType: 'JSON',
        success: function ( resp ) {
            $.each(resp, function(i, content){
                var posttitle = '<h3><a href="' + content.guid.link + '">' + content.title.rendered  + '</a></h3>';
                var postcontent = '<div class="content">' + content.excerpt.rendered + '</div>';
                $('.posts').append(posttitle+postcontent);
            })
        }
    });
});