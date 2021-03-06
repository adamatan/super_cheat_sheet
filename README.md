# Super cheat sheet 

- [awk](#awk)
- [bash](#bash)
- [find](#find)
- [grep](#grep)
- [jar files](#jar-files)
- [json](#json)
- [OSX terminal](#osx-terminal)
- [parallel](#parallel)
- [ssh](#ssh)
- [svn](#svn)
	- [GUI diff (Tested on OSX)](#gui-diff-tested-on-osx)
- [tr](#tr)
- [vim](#vim)
- [wget](#wget)
- [xmllint](#xmllint)
- [zip](#zip)

## awk

Usage: `cat input_file | awk -f script.awk`.

#### Print file starting from a regex match

	BEGIN       { should_stop=0;             }
	            { if (should_stop==0) print; }
	/<creative/ { should_stop=1;             }

#### Print file between two delimeters

Prints the lines between the first occurance of the first delimeter and the first occurance of the second delimeter. For actual XML files, [xmllint](#xmllint) is better.

	BEGIN           { should_print=0;                               }
	                { if (should_print==1)  print;         	        }
	/<creative/     { if (should_print==0) {should_print=1; print}  }  # No closing ">" - might have attributes!
	/<\/creative>/  { should_print=-1                            	}

## BASH scripting

Great [reference for operators](http://tldp.org/LDP/abs/html/refcards.html).

## find

	find . -type d -depth 1		# Direct subirectories of .
	find -name ".classpath"		# Files and dirs whose name is EXACTLY ".classpath"
	
#### exec

`exec` runs a command for each item found in `find`. 

	# greps each file, even if its name starts with "--"
        find  -type f -exec grep -H "http://feed.dp.yieldmanager.net/tools/pipesv2csv.php" '{}' \;
	
	
## grep

	grep -v "pixel" filename		# InVerse grep (lines w/o "pixel")
	grep -i "pixel" filename		# Case-Insensitive grep ("Pixel" also matched)

## jar files

Print classes and methods in a jar file. Credit: [SO question 3248335](#http://stackoverflow.com/questions/3248335/how-to-view-the-method-members-of-a-class-within-a-jar-file-thru-the-command-lin).

	export CLASSPATH=PATH_TO_JAR && \
	jar tvf $CLASSPATH | awk '{print $8}' | grep class$ | sed 's/\.class$//' | xargs javap | grep -v "Compiled from"

## json

	# Pretty-print (Credit: http://stackoverflow.com/questions/352098/how-to-pretty-print-json-from-the-command-line)
	echo '{"foo": "lorem", "bar": "ipsum"}' | python -mjson.tool


## OSX terminal

	sips -Z 640 *.jpg	# Resize *.jpg 640 pixels, IN PLACE - CREATE A COPY FIRST. http://goo.gl/luWx4

## parallel

	# Run script.sh for each lien of arguments in args.sh, show eta, at most 10 instances concurrently
	cat args | parallel -P 10 --eta ./script.sh {} 

## ssh

	ssh -q -o BatchMode=yes -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no   # Batch mode, insecure

## svn
	
	svn propset svn:executable ON sync.py	# Make a file executable
	svn log -l 10				# Last 10 log entries
	
### GUI diff (Tested on OSX)

Put the following code ([credit](http://dtobi.wordpress.com/2010/05/27/use-filemerge-with-svn-diff/)) in a shell file:

	#!/bin/bash
	
	DIFF="$(which opendiff)"
	$DIFF $6 $7

Name it `svndiff`, and put it anywhere in the path. The following command should open a GUI diff for svn:

    svn diff --diff-cmd svndiff

## tr
	printf "a\nb\nc\n" | tr "\n" " "        # Convert newlines to spaces
	printf "a       b     c" | tr -s " "    # Squeeze spaces (multiple spaces -> one space)

## vim
	
	map <F2> :tabn<CR><Esc>     # F2 switches tabs
	map <F3> :tabe              # F3 open filename in new tab

## wget

	# Download entire site recursively. Don't forget to reconfigure "--domains" with your site. Credit: Linux Journal, http://www.linuxjournal.com/content/downloading-entire-web-site-wget
	wget --recursive --no-clobber --page-requisites --html-extension --convert-links --domains ruby.learncodethehardway.org --no-parent http://ruby.learncodethehardway.org/book


## xmllint

	# Format XML
	xmllint --format filename
	
	# Print XPath tag
	xmllint --xpath "//city" <file>
	
	# Validate XML with its XSD schema (--noout : we don't need to print the XML itself)
	xmllint --noout --schema ProductConfiguration.xsd RedCar.xml
	
## zip

	zip file.zip file			# Compress
	unzip file.zip				# Decompress
