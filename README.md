# Flattr for Hyde
## A Flattr auto submit layout for the static site generator Hyde.

You can add these files to your Hyde setup to automagically generate flattr buttons for all your blog posts.
They will not appear on Flattr.com until some has flattred them. 

Written during the Flattr.com Open Source day!

If something is unclear please look in the included example project (forked from the Hyde repository https://github.com/lakshmivyas/hyde). 

## Install

Add the file 

	_flattr_button.html

to you layout skeleton folder.

Then you have to add the following variables to your settings file (or just use the one included)
	
	FLATTR_USER = "user-id"
	FLATTR_CAT = "text"
	FLATTR_DESCRIPTION = "A blogpost from my blog!"
	FLATTR_TAGS = "blog, text"

	CONTEXT = {
		'GENERATE_CLEAN_URLS': GENERATE_CLEAN_URLS,

		'FLATTR_USER' : FLATTR_USER, 
		'FLATTR_CAT' : FLATTR_CAT,
		'FLATTR_TAGS' : FLATTR_TAGS,
		'FLATTR_DESC' : FLATTR_DESCRIPTION,
	#	'FLATTR_COMPACT_BUTTON' : "True" #Uncomment this line to get compact button

	}



Change the "user-id" to your username on flattr.
You can change the other variables to something more appropriate as well. 
If you want the compact button instead of the normal flattr button, uncomment the last line in the CONTEXT dictionary. 

The Flattr javascript file must also be present on the website. I placed the code (below) in the
 
	_base.html
	
layout file. Here is the scipt that I added. 

	<script type="text/javascript">
	/* <![CDATA[ */
	    (function() {
	        var s = document.createElement('script'), t = document.getElementsByTagName('script')[0];
	        s.type = 'text/javascript';
	        s.async = true;
	        s.src = 'http://api.flattr.com/js/0.6/load.js?mode=auto';
	        t.parentNode.insertBefore(s, t);
	    })();
	/* ]]> */
	</script>

Now you can simply put 

	{% include "skeleton/_flattr_button.html" %}

where ever you want the Flattr button. In the included example I placed it on the bottom of the 

	_post.html

layout file in the example. 