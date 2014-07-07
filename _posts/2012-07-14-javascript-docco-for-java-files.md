---
layout: javascript

title: Docco For Java

description: Really simple but inelegant hack to use Docco for Java source files. Produce literate programming style documentation for your Java programs

excerpt: 

tags:
- Tools
- Literate
- Programming

categories:
- JavaScript

---

Docco is a quick-and-dirty, hundred-line-long, literate-programming-style documentation generator. It produces HTML that displays your comments alongside your code. It can be used to generate documentation for JavaScript, CoffeeScript, Python and Ruby. But it won't work for Java source files. There are ports of this script so that it can work with other languages, including Java, some prominent projects are [Jocco](https://github.com/Krilivye/Jocco) and [Marginalia (for Clojure)](http://blog.fogus.me/2011/01/05/the-marginalia-manifesto/).

The solution on this page is a hack. It is not a port of Docco for Java the way Jocco or Marginalia is. There, you've been warned.

# The hack

Get nodejs and the node package manager. Docco depends on this. It can be installed via brew or by downloading the binary installer from http://nodejs.org. The binary installer already includes npm.

`brew install -g node`

`brew install -g npm`

Get Docco via npm

`sudo npm -g install docco`

Intall pygments

`sudo easy_install pygmnets`

Locate the docco script

`ls -l `which docco` `

The script is over at /usr/local/lib/node_modules/docco/lib/docco.js. Edit the script and add the `.java` entry to the languages object literal.

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

This is somewhere between line 98 to line 120. Java was not there, it was added so docco generate nice docs for Java source files. Remember to write your comments using the C++ style (//). Docco will not parse the comments using JavaDoc style or C style comment block.

Using docco is very simple, run it against any supported file, for example

`docco MyProgram.java`

To learn more about Docco, head over it's [github page](http://jashkenas.github.com/docco/)

# References

1. Jeremy Ashkenas, "Docco", http://jashkenas.github.io/docco

