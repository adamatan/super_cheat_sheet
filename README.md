My polyglot cheat sheet
=======================

zip
---

	zip file.zip file			# Compress
	unzip file.zip				# Decompress


awk
---

Print file till a regex ("`Full`") is matched.

	BEGIN    { should_stop=0;              }
	         { if (should_stop==0) 	print; }
	/Full/   { should_stop=1;              }
	
grep
----

	grep -v "pixel" filename		# InVerse grep (lines w/o "pixel")
	grep -i "pixel" filename		# Case-Insensitive grep ("Pixel" also matched)

OSX terminal
------------

	sips -Z 640 *.jpg	# Resize *.jpg 640 pixels, IN PLACE - CREATE A COPY FIRST. http://goo.gl/luWx4

wget
----

	# Download entire site recursively. Don't forget to reconfigure "--domains" with your site. Credit: Linux Journal, http://www.linuxjournal.com/content/downloading-entire-web-site-wget
	wget --recursive --no-clobber --page-requisites --html-extension --convert-links --domains ruby.learncodethehardway.org --no-parent http://ruby.learncodethehardway.org/book


xmllint
-------

	# Format XML
	xmllint --format filename
	
svn
---

	svn log -l 10			# Last 10 log entries
	
	
json
----

	# Pretty-print (Credit: http://stackoverflow.com/questions/352098/how-to-pretty-print-json-from-the-command-line)
	echo '{"foo": "lorem", "bar": "ipsum"}' | python -mjson.tool 
