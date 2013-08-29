**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [My polyglot cheat sheet](#my-polyglot-cheat-sheet)
	- [awk](#awk)
	- [find](#find)
	- [grep](#grep)
	- [json](#json)
	- [OSX terminal](#osx-terminal)
	- [ssh](#ssh)
	- [svn](#svn)
		- [GUI diff (Tested on OSX)](#gui-diff-tested-on-osx)
	- [tr](#tr)
	- [wget](#wget)
	- [xmllint](#xmllint)
	- [zip](#zip)

# My polyglot cheat sheet

## awk

Print file till a regex ("`Full`") is matched.

	BEGIN    { should_stop=0;              }
	         { if (should_stop==0) 	print; }
	/Full/   { should_stop=1;              }

## find

	find . -type d -depth 1		# Subirectories of .
	
## grep

	grep -v "pixel" filename		# InVerse grep (lines w/o "pixel")
	grep -i "pixel" filename		# Case-Insensitive grep ("Pixel" also matched)
	
## json

	# Pretty-print (Credit: http://stackoverflow.com/questions/352098/how-to-pretty-print-json-from-the-command-line)
	echo '{"foo": "lorem", "bar": "ipsum"}' | python -mjson.tool


## OSX terminal

	sips -Z 640 *.jpg	# Resize *.jpg 640 pixels, IN PLACE - CREATE A COPY FIRST. http://goo.gl/luWx4

## ssh

	ssh -q -o BatchMode=yes -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no   # Batch mode, insecure

## svn

	svn log -l 10			# Last 10 log entries
	
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

## wget

	# Download entire site recursively. Don't forget to reconfigure "--domains" with your site. Credit: Linux Journal, http://www.linuxjournal.com/content/downloading-entire-web-site-wget
	wget --recursive --no-clobber --page-requisites --html-extension --convert-links --domains ruby.learncodethehardway.org --no-parent http://ruby.learncodethehardway.org/book


## xmllint

	# Format XML
	xmllint --format filename
	
## zip

	zip file.zip file			# Compress
	unzip file.zip				# Decompress
