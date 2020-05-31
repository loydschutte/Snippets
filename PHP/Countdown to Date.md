<?php

$dt_end = new DateTime('December 3, 2016 2:00 PM');
$remain = $dt_end->diff(new DateTime());
echo $remain->d . ' days and ' . $remain->h . ' hours';

?>