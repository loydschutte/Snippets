  function unifyHeights() 
  {
    var maxHeight = 0;
    $('div#OuterContainer').children('div').each(function(){
      var height = $(this).outerHeight();
      //alert(height);
      if ( height > maxHeight ) { maxHeight = height; }
    });
    $('div.innerDivs').css('height', maxHeight);
  }