Use this function to easily sort an array. We'll use slice to create a copy of the array so we don't hurt our data. After you've sorted pass variablename into a render function to rerender your page with the sorted data from variablename.
    
    let variablename = arrayname.slice().sort(function(a, b){
        return a.name.localeCompare(b.name);
    })