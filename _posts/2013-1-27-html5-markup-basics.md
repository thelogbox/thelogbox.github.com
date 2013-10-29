---
layout: html5

title: Markup Basics

description: Introduction to HTML5 elements and basic HTML construct

tags:
- Markup
- Elements

categories:
- HTML5

---

A markup is something that you add to plain text to alter its presentation, either on print or on screen. For the older audience, you probably could remember WordStar &mdash; when you use CTRL-B to give instruction to the printer to render it in **bold face**, that was a markup instruction. 

An HTML file is text file, more specifically a marked up text file. The markup instructions are called *tags*, sometimes they are also referred to as **HTML elements* or elements for short, so we will start using those terms already. The tags are meant to be understood by web browsers, each tag defined in the HTML standard language means something to the browser. In order to use the markups effectively, you need to know what the tags are supposed to do.

HTML is a language, but not in a way like JavaScript or Java or C is a language. It is a markup language, it has structures and rules that you need to observe. 

# Basic structure 

{% highlight html %}
<!DOCTYPE html> 
<html>
  <head> 
  </head>

  <body>
  </body> 
</html>
{% endhighlight %} 
  
The \<html\> element is the outermost element in a document, there can only be one pair of this element inside an HTML source file. There are two elements that can be nested inside the html tag, the **\<head\>** and the **\<body\>** elements.

All the visible things that you want to show on an HTML page goes to the body element. For example, ordered lists, un-ordered lists, headings, paragraphs, tables.

Things written inside the head element will not be visible on the HTML page. That is not to say they are less important. Some of the things you may find on the head element are script–for embedding Javascript codes, link–for CSS amongst other things, title etc. 

You probably noticed that the tags came in pair. The opening \<body\> tag is paired with the closing \</body\> tag. It is important to remember that HTML markup always (almost) comes in pairs, lest, you will have some unpredictable results.

## DOCTYPE
The *\<!DOCTYPE\>* is not the same as the other tags, it is an instruction to the processor (the web browser) that contains which version of HTML the document is using. This declaration is necessary because there is more than one version of HTML. The HTML technology has been evolving for the past two decades. The current version of HTML is 5, but it doesn’t mean that all web pages are now using HTML version 5. Some web pages are still coded using previous versions of HTML, that is the reason why the browser needs to know which version it is dealing with. 

## Versions of HTML 

1. HTML - 1991
2. HTML+ - 1993
3. HTML 2.0 - 1995 
4. HTML 3.2 - 1997 
5. HTML 4.01 - 1999 
6. XHTML 1.0 - 2000
7. HTML5 - 2012
8. XHTML5 - 2013

The [W3C][versionshtml] site maintains an up to date list of HTML versions.

The way to declare a DOCTYPE in HTML 5 is <!DOCTYPE html>, you can already use this now. It wasn't always this simple to declare a DOCTYPE, the previous versions of HTML required some pretty involved and almost cryptic entries for this. Fortunately, current browsers will look at the HTML5 DOCTYPE and switch to standards mode, this method of doctype declaration can already be used. What this means is that the HTML5 pages you will write today can last for a very long time.

There are other ways to declare DOCTYPE for the other versions of HTML, [W3C keeps an updated page information on doctypes] [doctypeversions] if you need some historical reference.

# Common tags 

1. \<h1\> - Heading, the most important and most emphasised of the all heading tags
2. \<h2\> - another heading, less important than \<h1\> but more important than;
3. \<h3\>
4. \<strong\> - display something in bold face
5. \<em\> - display something in italics (emphasised)
6. \<ol\> - display a list, a numbered (ordered) one
7. \<ul\> - another list, but an unordered one. It doesn't have numbers before the items, they just display dots or squares
8. \<li\> - this is an item on a list. You have to use this inside an ordered list or an unordered list, it will be meaningless if written outside *ol* or *ul*
9. \<p\> - a paragraph break
10. \<br\> - a line break

**GOOD TO KNOW**: HTML is not case sensitive but it's a good idea to write the tags in lowercase. The World Wide Web Consortium (W3C) *recommends* lower in HTML4 and **demands** lowercase in XHTML.

# Attributes

Sometimes tags are not written plainly as a word enclosed in a pair of \< \> like \<h1\>. Sometimes they contain some additional information about the HTML element. This additional information is called an attribute. 

For example, in the tag *\<a href="http://thelogbox.com"\>thelogbox\<a\>* &mdash; **a* is the tag used to denote a hyperlink, it will make you jump to another location.  The jump can to a location on the same document, to a location on a completely new document on the same domain or to a new document on another domain. The *href* is the attribute, it tells the hyperlink tag where exactly to jump.

**GOOD TO KNOW**:

- There are lots of elements that can have attributes
- Attributes are always written on the opening tag
- Attributes are a dictionary pair, it's a got a key (href) and a value (http://thelogbox.com), like in our example

# Exercise

Create a simple HTML file, like the one below. Name it first.html

{% highlight html %}
<!DOCTYPE html> 
<html>
  <head> 
  </head>

  <body>
    <h1>Hello World</h1>
    <p>
    The quick brown fox
    </p>
    <strong>jumped</strong> over the head of the
    <em>lazy dog</em> near the river bank
  </body> 
</html>
{% endhighlight %}

Open the file in your browser. You can simple double click the file in Explorer (Windows) or Finder (OSX). The *.html* extension will usually open the file in the default browser.

1. Omit the ending tag of *h1*, refresh the browser. See what happens, then put ending *h1* tag again
2. Omit the ending *body* tag, see what happens
3. Add an ordered list to your HTML file, place it right before the  closing *body* tag 
4. Make **Hello World** a hyperlink to **Google.com**
 
[versionshtml]: http://www.w3schools.com/html/html_intro.asp "HTML Versions"
[doctypeversions]: http://www.w3schools.com/tags/tag_doctype.asp "DOCTYPE declarations"