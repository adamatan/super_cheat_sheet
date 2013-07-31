My polyglot cheat sheet
=======================

zip
---

	zip file.zip file			# Compress
	unzip file.zip				# Decompress


awk
---

Print file till a regex (`Full`) is matched.

	BEGIN    { should_stop=0;              }
	         { if (should_stop==0) 	print; }
	/Full/   { should_stop=1;              }