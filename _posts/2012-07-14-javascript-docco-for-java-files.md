---
layout: javascript

title: How to hack Docco for Java

description: Really simple but inelegant hack to use Docco for Java source files. Produce literate programming style documentation for your Java programs

excerpt: 

tags:
- Tools
- Literate
- Programming

---



Docco is a quick-and-dirty, hundred-line-long, literate-programming-style documentation generator. It produces HTML that displays your comments alongside your code. It can be used to generate documentation for JavaScript, CoffeeScript, Python and Ruby. But it won't work for Java source files. There are ports of this script so that it can work with other languages, including Java, some prominent projects are [Jocco](https://github.com/Krilivye/Jocco) and [Marginalia (for Clojure)](http://blog.fogus.me/2011/01/05/the-marginalia-manifesto/).

The solution on this page is a hack. It is not a port of Docco for Java the way Jocco or Marginalia is. There, you've been warned.


**1. Get nodejs** and the **node package manager**. 

Docco depends those two. We can install these tools either by using **Homebrew** or by downloading the installation package of nodejs from http://nodejs.org

~~~
$ brew install -g node
$ brew install -g npm
~~~

**2. Get Docco** using the node package manager

~~~
$ sudo npm -g install docco
~~~

**3. Install pygments**

~~~
$ sudo easy_install pygments
~~~

**4. Edit the docco script**



The script file of docco can be usually found at  /usr/local/lib/node_modules/docco/lib/docco.js folder. 

Edit the script and add the **.java** entry to the languages object literal.

~~~
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
~~~

The code snippet above can be found somewhere between line 90 to line 120 of docco.js. The **java** entry was added so docco can generate nice docs for Java source files. 

Remember to write your comments using the C++ style (//). Docco will not parse the comments using JavaDoc style or C style comment block.

Using docco is very simple, run it against any supported file, for example

**5. Test it out**

    docco MyProgram.java`

## References

1. Jeremy Ashkenas, "Docco", http://jashkenas.github.io/docco

