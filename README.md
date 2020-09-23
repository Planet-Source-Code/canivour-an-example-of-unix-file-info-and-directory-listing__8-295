<div align="center">

## An Example of Unix file info and directory listing


</div>

### Description

Reads a directory ands makes a link to every file in the directory and shows some info on the file (Works best with Unix servers), see the screenshot for a better understanding of what this looks like.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Canivour](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/canivour.md)
**Level**          |Beginner
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__8-2.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/canivour-an-example-of-unix-file-info-and-directory-listing__8-295/archive/master.zip)





### Source Code

```
<?
////////////////////////////////////////////////////////
//Coded by: Canivour////////////////////////////////////
//Coded on: 03.19.01////////////////////////////////////
//Coded while listening to: Slipknot - Wait and Bleed///
////////////////////////////////////////////////////////
////////////////////////////////////////////////////////
//Reads a directory and displays a link to every file///
//in the directory (other directories not included)/////
//and gives some info on the file, NOTE: Info works/////
//best on Unix systems (that should be obvious ;) //////
//Happy Coding//////////////////////////////////////////
////////////////////////////////////////////////////////
	//starting directory
	$startDir = "/home/canivour/html";
	//open directory
	$openDir = opendir($startDir);
	//variable that holds the number of free bytes in the directory
	$freeSpace = diskfreespace($startDir);
	print "<center>";
	print "<b>Current Directory: ".$startDir."</b><br>"; //Current Directory
	print "<b>Free space in directory ".$startDir.": ".$freeSpace." bytes\n"; //Free space
	print "<table border=0 cellspacing=1 cellpadding=4>\n<tr>\n<td>\n"; //starting of table
	print "<font>Files</font>";
	print "<table border=1 bordercolor=#777777 cellspacing=2 cellpadding=4>\n"; //another table
	//loop while there are still things to be read in directory
	while($path = readdir($openDir))
	{
		//gets the base name of file i.e instead of /home/canivour/html/index.html its index.html
		$file = basename($path);
		//makes sure we dont we read the . and .. direcotry (current directory and parent directory)
		if($file!="." && $file!="..")
		{
			//if its not a directory print out the stats (can be changed for your needs)
			if(!is_dir($startDir."/".$file))
			{
				$fullDir = $startDir."/".$file; //full directory path of file
				$statCheck = stat($fullDir); //keeps info on files
				print "<tr bgcolor=#777777><td>\n";
				print "<a href=".$file.">".$file."</a>\n"; //link to name of file
				print "</td></tr>\n";
				print "<tr><td>\n";
				print "Owner Id: ".$statCheck[5]."\n &nbsp&nbsp&nbsp"; //owner id is stored in the 5th element automatically
				print "Group Id: ".$statCheck[6]."\n &nbsp&nbsp&nbsp"; //group id is stored in the 6th element automatically
				print "Inode: ".$statCheck[2]."\n &nbsp&nbsp&nbsp"; //inode is stored in the 2nd element automatically
				print "</td></tr>\n";
			} //end if
		} //end if
	} //end while
?>
```

