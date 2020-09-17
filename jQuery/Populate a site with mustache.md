    $(function(){
    var data;
    $.getJSON("./templates/ourdata.json")
    .done(function(ourData) {
        render();
        })
        .fail(function() {
            console.log( "error",arguments);
        })
        .always(function() {
            console.log( "success" );
        });
        function render(){
            $.get('./templates/ourtemplate.tmpl', function(mydata){
                var tmpl = mydata;
                var ourstuff = Mustache.render(tmpl, data);
                $('#codeblockid').append(ourstuff);
                
            });
        }
    });
