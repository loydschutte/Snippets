Create a simple EventListener that listens for CLICK event on the node.

This replaces .click() in jQuery.

    let ourItem = document.querySelector('#node-name');
    ourItem.addEventListener('click', ()=> {
        doSomething();
    })