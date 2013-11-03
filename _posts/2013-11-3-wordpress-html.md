---
layout: wordpress

title: Introduction to HTML

description: A small introduction to HTML. Just the basics you need for WordPress

excerpt: 

tags:
- html

author: Ted Hagos

categories:
- WordPress
---

I'm hoping and dangerously assuming that you have some knowledge of HTML or at least have a passing appreciation of it &mdash; at least what it looks like and what it is used for. That will spare us the dry details of description.

While we can dodge the academic description of the markup language, a passing appreciation of the language will not do. Not if you are a developer. You will need to know more. Just a bit more.

HTML is not a programming language. It is a markup language. That is our first fact about HTML.

Marking up has its roots in the publishing industry, the paper publishing industry that is. Before the age of electronic publishing, a document needs to go through several processes before it lands on your lap either as book or magazine, or what have you. One of these processes is that an editor or somebody in charge of editing will go through a manuscript and scribble some instructions on the paper itself. These instructions could be “underline that word”, “emphasize this”, “make this phrase stand out”. Of course when the document is published the reader will not see those instructions. What they saw was just the resulting published document. Those instruction were meant for somebody to carry out, I suppose the typesetter would have carried them out before the final plates were rolled over and mass-produced.

Marking up means adding instructions to a document, more specifically adding presentation instructions to a document so that some of its parts are underlined, emphasized or highlighted.

HTML is a modern way of marking up documents. It was first thought of by Tim Berners Lee during his stay at CERN. The history of HTML, while an interesting read is simply not part of the scope of this document so I will refer you to the trusty Wikipedia page for [HTML history](http://en.wikipedia.org/wiki/HTML) for an extended reading session about the origins and evolution of HTML. For our purpose, I would like to address the technical aspects of it and how it will help us build Wordpress apps.

## GETTING STARTED

I need you to remember the folder where you installed WAMP. If you followed the instruction during the setup chapter, that folder would be in *C:\Users\yourname\wamp*. Go to that folder. You will find another folder called *www* inside it. Go to the www folder. 

Create a folder inside *www*, name it *practice*. This is where we will store all our practice files. 

Create a file and name it *first.html*. Launch a program editor to open first.html for editing. Do not double click first.html. Double clicking will open the file for viewing. Most likely it will launch your default browser and view the file. That is not what we want to do right now. You may right-click on the file to open Window's context menu, then choose a program editor to open the html file. Edit it and write the following

{% highlight html %}
<!doctype html>
<html>

  <h1>Hello</h1>

</html>
{% endhighlight %}
<div id='lst'>first.html</div>

Don't worry about the contents for now. They will be discussed soon enough. We are simply making sure that our tools are working properly. 

Double click first.html. Your browser would have launched. You have just created your first HTML document.

## STRUCTURE AND COMPOSITION

Words inside angle brackets &mdash; *&lt; like this &gt;*  &mdash; are instructions. They are part of the HTML language. They have special meaning to the browser. When the browser reads a pair of angle brackets, it will carry out an instruction. So things inside these brackets are what might you might call special words. Although developers refer to them as *tags* or *elements*. You better get used to calling them that as well.

You might have noticed that the instructions come in pairs. They don't always do &mdash; like in the case of the &lt; !doctype &gt;. But most of the time instructions come in pairs.

Don’t worry about the doctype yet, we won’t get into that right now because its gory details will lead us into the rabbit hole of XML and SGML — don’t worry about those two either. They are not important to you for now. The doctype is basically a declaration of what kind of document the file is. In this case, it says HTML.

***

The fundamental structure of an html document is as follows


{% highlight html %}
<!doctype html>
<html>

</html>
{% endhighlight %}
<div id='lst'>basic structure</div>

Whatever it is that you will write inside an HTML doc has to be inside the paired html tags. It doesn’t make sense to put anything outside of them except DOCTYPE.

Elements can be nested within other elements. Whatever it is that you will put in between the html root tags will be tags as well.

There some more structural issues that we need to get out of the way before we can take a look at the presentation semantics of HTML. A more complete structure for an HTML doc looks like the following

{% highlight html %}
<!doctypehtml>
<html>
  <head> <title>First</title>
  </head>
  
  <body>
    <h1>Hello</h1> 
  </body>
</html>
{% endhighlight %}
<div id='lst'>HTML doc structure</div>

An HTML doc will have two major parts. The HEAD and the BODY.
The BODY part contains most of the things you see on a web page. It has the meat and potatoes of the web content. This is where your headings, footers, videos, paragraph content and others.

The HEAD part is not entirely visible to the visible. With the exception of title tag, nothing inside the head part can be seen on a web page. The HEAD contains structure and meta information about the page while the BODY has the content.

![HTML head and body](/img/wordpress/html-head-body.png)
<div id='lst'>head and body part</div>

If you edited our *first.html* practice file and followed along, you can try viewing the result of the edited document so you can see the results in your browser. 





