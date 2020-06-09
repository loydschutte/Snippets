<?php 

require('simple_html_dom.php');

$html = file_get_html('https://www.youtube.com/user/caseyneistat/videos');

$videos = [];

// Find top ten videos
$i = 1;
foreach ($html->find('li.channels-content-item') as $video) {
        if ($i > 100) {
                break;
        }
 
        // Find item link element 
        $videoDetails = $video->find('a.yt-uix-tile-link', 0);
 
        // get title attribute
        $videoTitle = $videoDetails->title;
 
        // get href attribute
        $videoUrl = 'https://youtube.com' . $videoDetails->href;
 
        // push to a list of videos
        $videos[] = [
                'title' => $videoTitle,
                'url' => $videoUrl
        ];
 
        $i++;
}
 

foreach($videos as $video){
	echo '<a href="' . $video['url'] . '"> ' . $video['title'] . '</a>';
		echo "<br />";
}
?>