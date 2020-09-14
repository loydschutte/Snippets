Target a buttons click event. When the button is clicked grab the innerHTML(value) of all matching CSS subselectors and log their value to the console.

This replaces val() in jQUery.

    let updateButton = document.querySelector('button');
        updateButton.addEventListener('click', ()=> {
        let ourContents = document.querySelectorAll('#ourid span');
        ourContents.forEach(function(arrayItem){
        console.log(arrayItem.innerHTML);
        })
    })