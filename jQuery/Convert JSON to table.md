function ConvertToTable(jData) {
  var arrJSON = typeof jData != 'object' ? JSON.parse(jData) : jData;
  var $table = $('');
  var $headerTr = $('');

  for (var index in arrJSON[0]) {
    $headerTr.append($(' ').html(index));
  }
  $table.append($headerTr);
  for (var i = 0; i < arrJSON.length; i++) {
   var $tableTr = $('');
    for (var index in arrJSON[i]) {
      $tableTr.append($(' ').html(arrJSON[i][index]));
    }
    $table.append($tableTr);
  }
  $('body').append($table);
}