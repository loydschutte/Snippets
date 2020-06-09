$("#age-verify").submit(function() {
    var day = $("#day").val();
    var month = $("#month").val();
    var year = $("#year").val();
    var age = 21;
    var mydate = new Date();
    mydate.setFullYear(year, month - 1, day);
    var currdate = new Date();
    currdate.setFullYear(currdate.getFullYear() - age);
    if ((currdate - mydate) & lt; 0) {
        alert("Sorry, only persons over the age of " + age + " may enter this site");
        return false;
    }
    return true;
});