var wpApp = document.getElementById('wpapp');
var xmlhttp = new XMLHttpRequest();
var url = "http://192.168.33.10/build/wp-json/wp/v2/pages";

xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        var myArr = JSON.parse(this.responseText);
        myFunction(myArr);
    }
};
xmlhttp.open("GET", url, true);
xmlhttp.send();

function myFunction(arr) {
    var out = "";
    var i;
    for(i = 0; i < arr.length; i++) {
    	if(arr[i].slug=="home"){
        out += '<h3><a href="' + arr[i].link + '">' + arr[i].title.rendered  + '</a></h3>' + 
        '<div class="content">' + arr[i].content.rendered + '</div>';
	    };
    }
    wpApp.innerHTML = out;
}