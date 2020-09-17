Basic layout for using Twitter's Typeahead to pull data from a remote source, bind it to html form input elements within a page and verify that data input only matches what's in the source database.

    var myData = new Bloodhound({
        datumTokenizer: Bloodhound.tokenizers.whitespace,
        queryTokenizer: Bloodhound.tokenizers.whitespace,
        prefetch: './search/data.php'    
    });

    $('input').typeahead(null, {
        name: 'myData',
        limit: 20,
        source: myData
    }).on('change blur', function(){
        
        var target = this;

        match = false;

        $.each(statutes.index.datums, function(target, item){
            if($(target).val() == item.name){
                match = true;
            }
        });

        if(!match) {
            $(target).val('');
        }

    });

    $('.typeahead').bind('typeahead:select', function(ev, suggestion) {
        console.log('Selection: ' + suggestion);
    });