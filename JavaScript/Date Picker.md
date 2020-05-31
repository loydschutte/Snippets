HTML Code:

<input type="date" id="dt" onchange="mydate1();" hidden/>
<input type="text" id="ndt"  onclick="mydate();" hidden />
<input type="button" Value="Date" onclick="mydate();" />


CSS Code:

#dt {
  text-indent: -500px;
  height: 25px;
  width: 200px;
}


Javascript Code :

function mydate() {
  //alert("");
  document.getElementById("dt").hidden = false;
  document.getElementById("ndt").hidden = true;
}

function mydate1() {
  d = new Date(document.getElementById("dt").value);
  dt = d.getDate();
  mn = d.getMonth();
  mn++;
if(dt < 10){
    dt = ('0' + dt).slice(-2); 
  };

  if(mn < 10){
    mn = ('0' + mn).slice(-2); 
  };

  yy = d.getFullYear();
  document.getElementById("ndt").value = dt + "/" + mn + "/" + yy
  document.getElementById("ndt").hidden = false;
  document.getElementById("dt").hidden = true;
} 