Find a date in the future and make sure the day falls on a weekday.

    function checkDay($appearancedate){
        $dt1 = strtotime($appearancedate);
        $dt2 = date("l", $dt1);
        $dt3 = strtolower($dt2);
        if(($dt3 == "saturday" )|| ($dt3 == "sunday"))
            {
                $result = false;
            } else {
                $result = true;
            }
            return $result;
        }

    function getDay($appearancedate){
        $dt1 = strtotime($appearancedate);
        $dt2 = date("l", $dt1);
        $dt3 = strtolower($dt2);
        if(($dt3 == "saturday" )|| ($dt3 == "sunday"))
            {
                $result = $dt3;
            } else {
                $result = $dt3;
            }
            return $result;
    }

    $savestheday = Date('Y-m-d h:i:s');// todays date
    $splitdate = preg_split('/[ ]/', $savestheday);
    $newdate = new DateTime($splitdate[0]);

    $day = $newdate->format('d');
    $month = $newdate->format('m');
    $year = $newdate->format('Y');

    $courtmonth = $month + 4;

    if($courtmonth>12){
        $courtmonth = $courtmonth-12;
        $year = $year + 1;
        $appearancedate = $year."-".$courtmonth."-".$day;
        $result = checkDay($appearancedate);
        if($result==false){
            $appearancedate = $year."-".$courtmonth."-".($day + 02);
        }
    }
    $weekday = ucwords(getDay($appearancedate));
    echo $appearancedate . " " . $weekday;