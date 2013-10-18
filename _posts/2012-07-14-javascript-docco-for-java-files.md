---
layout: post

title: Docco For Java

description: 

excerpt: 

categories:
- blog

---

Docco is a quick-and-dirty, hundred-line-long, literate-programming-style documentation generator. It produces HTML that displays your comments alongside your code. It can be used to generate documentation for JavaScript, CoffeeScript, Python and Ruby---but it won't work for Java files. 

If you are looking for the clean and proper way to generate docco-style docs for Java source files, this guide is not what that is&mdash;this is a hack of docco to make it work with Java source files. You could take a look at [Jocco](https://github.com/Krilivye/Jocco) or [Marginalia (for Clojure)](http://blog.fogus.me/2011/01/05/the-marginalia-manifesto/)

If you really want to use docco to generate documentation for .java files, you can;

1. Rename the .java to .js (temporarily)
2. Run the docco app against the renamed .java files (.js file right now)
3. Edit the resulting HTML file and replace the *title* and first *H1* to reflect the name of your Java file
4. Rename the .js file back to .java file---lest you get into trouble

You can do all 4 steps above, provided that you write your comments in C++ style (**//** comment). Or you can tweak the docco script just a little bit so that it reads .java files as well--this is what this text is all about.

# HACKING DOCCO

I am using an OSX machine, so these steps were done using OSX 10.8; I think these things should be applicable to a Linux machine as well. The steps below are done in the Terminal.app

1. Get Node.JS (docco depends on this). If you installed *brew* you can simply run **brew install node*. If not, head over to http://nodejs.org, there is a .pkg download for OSX. The .pkg installation includes the **npm** tool, which you will need

2. Install Pygments. You can use *easy_install* to get Pygments; easy_install is part of the [Python setuptools](http://pypi.python.org/pypi/setuptools). When you already got the easy_install tool, run **sudo easy_install pygments** on the terminal

3. Install docco using npm **sudo npm -g install docco**

4. Try to find the docco script **which docco**. It will point you to /usr/local/bin/docco. If you list docco using  the -l flag, like so **ls -l /usr/local/bin/docco**, you will notice that it is a link to */usr/local/lib/node_modules/docco/bin/docco*. This is the docco the script, but it is not the main script. The main script is at */usr/local/lib/node_modules/docco/lib/docco.js*

5. Open docco.js, and add the .java entry to the **languages** object literal. 

{% highlight javascript %}

  languages = {
    '.coffee': {
      name: 'coffee-script',
      symbol: '#'
    },
    '.js': {
      name: 'javascript',
      symbol: '//'
    },
    '.rb': {
      name: 'ruby',
      symbol: '#'
    },
    '.py': {
      name: 'python',
      symbol: '#'
    },
	'.java': {
		name: 'java',
		symbol: '//'
	}
  };

{% endhighlight %}

This is somewhere between line 98 to line 120. Java was not there, it was added so docco generate nice docs for .java files. 

Just remember to write your comments using the C++ style (//). Docco will not parse the comments using JavaDoc style or C style comment block. Using docco is very simple, run it against any supported file e.g. **docco MyProgram.java** or **docco MyProgram.js**.


To learn more about Docco, head over it's [github page](http://jashkenas.github.com/docco/)


