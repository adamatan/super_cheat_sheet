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
