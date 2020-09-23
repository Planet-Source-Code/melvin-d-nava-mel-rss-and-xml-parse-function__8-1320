<div align="center">

## MEL :: RSS And XML Parse Function


</div>

### Description

**UPDATED** This function will parse your favorite XML and RSS news feeds in a nice format. Only one variable to set up and easy to integrate and modify. Tested on several sources. Let me know this has been useful. Comments and suggestions are very much appreciate it. **Please Vote**
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Melvin D\. Nava](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/melvin-d-nava.md)
**Level**          |Intermediate
**User Rating**    |5.0 (40 globes from 8 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Data Structures](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/data-structures__8-8.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/melvin-d-nava-mel-rss-and-xml-parse-function__8-1320/archive/master.zip)





### Source Code

```
<?php
//
// The Function
// By Melvin D. Nava
// http://mdnava.network.com.ve/
//
function parse_rss($f) {
	$xmlfile = fopen($f, 'r');
	if (!$xmlfile) die('cannot open the xml file');
	$readfile = fread($xmlfile ,40000);
	$parsefile = eregi("<item>(.*)</item>", $readfile ,$arrayreg);
	$filechunks = explode("<item>", $arrayreg[0]);
	$count = count($filechunks);
	echo '<font face=verdana><ul>';
	for($i=1 ; $i<=$count-1 ;$i++) {
		ereg("<title>(.*)</title>",$filechunks[$i], $title);
		ereg("<link>(.*)</link>",$filechunks[$i], $links);
		ereg("<description>(.*)</description>",$filechunks[$i], $description);
		echo str_replace('hxaxh','a',"<li><font style='font-size: 12px;'><hxaxh target=_blank href ='$links[1]'\>".utf8_decode($title[1])."</hxaxh></font>");
		echo "<br><font color=gray style='font-size: 10px;'>".utf8_decode($description[1])."</font></li>";
	}
	// feel free to remove next notice
	// is not needed by this function
	echo '</ul><font style="font-size: 10px;">Better News Grabber by ';
	echo str_replace('hxaxh','a','<hxaxh target=_blank href="http://mdnava.network.com.ve/">Melvin D. Nava</hxaxh></font></font></font>');
}
//
// The Example
//
echo '<h1>Star Wars News</h1>';
$xmlfeed = 'http://www.starwars.com/community/webmasters/starwars.rdf';
parse_rss($xmlfeed);
?>
```

