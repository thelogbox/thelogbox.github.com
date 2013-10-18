---
layout: post

title: JavaScript Toolchain

description: 

excerpt: 

categories:
- web-development

---


*NOTE:*

- **Platform** - OSX 10.8 (Mountain Lion)
- **Editor(s)** - TextMate 2.0 Alpha, Smultron4
- **JavaScript Environments** - SpiderMonkey, RingoJS, NodeJS, Rhino
- **Code checker** - JSLint (via JavaScript tools)

# Node.JS 

1. Go to nodejs.org, download the tar.gz version, then **make install**. This way, the npm installer is also intalled. Yes you can try brew install node, but there were some problems installing the npm. Just the get the source and install using the make tools, like you used to. There is also a .PKG installer, this one is more painless than the source install--use the PKG whenever possible

2. Get docco - sudo install -g docco

3. If you encounter some 404 problems on the registry of npm, you can change the registry. Default registry is npm set registry http://registry.npmjs.org/ , I had to try either one of these two

- npm set registry http://85.10.209.91/
- npm set registry http://165.225.128.50:8000

# JavaScript tools for TextMate 

1. on the CLI, cd to *~/Users/ted/Library/Application Support/TextMate/Managed/Bundles*. On 1.x version of TextMate, this directory could have been *~/Library/Application Support/TextMate/Pristine Copy/Bundles*

2. git clone https://github.com/subtleGradient/javascript-tools.tmbundle.git

3. Bundle should have been reloaded by now, if not


# PhantomJS 

http://phantomjs.org, this is good for

- headless web testing
- site scraping
- SVG rendering
- network monitoring

# Test tools

- Jasmine
- QUnit
- FuncUnit
- YUI Test 

There are some [quick info on](http://code.google.com/p/phantomjs/wiki/TestFrameworkIntegration). There is also some [quickstart docs at](http://code.google.com/p/phantomjs/wiki/QuickStart)



# Test Web servers 

Ways to run a simple web server. This could be very handy if you are testing JavaScript and HTML5 

1. Python -- just run python -m SimpleHTTPServer on any directory. The dir becomes the docroot. http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python for more info
2. nanoc, of course
3. LAMP, WAMP or use the default Apache installation in OSX
4. Jetty - http://docs.codehaus.org/display/JETTY/Hightide+Documentation
5. Apache Tomcat, Jetty
6. [LightHttpd](http://redmine.lighttpd.net/projects/lighttpd/wiki/TutorialConfiguration)
7. Node - [Static file serving](http://www.sitepoint.com/serving-static-files-with-node-js/). What I probably will use for RD training is http-server. Just "sudo npm -g install http-server" then start with http-server. The current directory will be served up

