---
layout: post

title: Ruby Notes

description: 

excerpt: 

tags:
- RVM

categories:
- Ruby

---



# 1. Use the Ruby Version Manager (rvm)

Don't incur technical debt on this one, you will be sorry if you skip this step &mdash; that is for sure. Ruby has crept in lots development areas e.g. web programming, desktop and mobile programming. It has also made its way into lots of other runtimes e.g. JVM (JRuby, Mirah) and the CLR (IronRuby). The variety of these targets will require you to work with very specific versions of Ruby (1.9.x, 1.8.x, JRuby etc). It is impractical (and quite masochistic) to manage all these environments on your own and by hand. So just get the RVM 

OSX already ships with Ruby. In Linux (Debian specifically) I had to get it from a repo (*sudo apt-get install ruby*). For Windows, go to the [ruby-lang](http://www.ruby-lang.org/en/downloads/) site, there are instructions on how to get the rubyinstaller for Windows. 

Open up a terminal. 

<pre class="codeblock">

$ curl -L https://get.rvm.io | bash -s stable --ruby

# to see a list of things you can install
$ rvm list known

# to install ruby 1.9.3
$ rvm install 1.9.3

# to use ruby 1.9.3 instead of 
# the default 1.8.7
$ rvm use 1.9.3

# to use the default 1.8.7
$ rvm use system --default

# install a gem, no need for extra syntax
# just check the version of ruby you are using
# before doing anything 

$ ruby -v
$ rvm use 1.9.3
# ensure that the gems are updated before installing 
# anything
$ gem update --system
$ gem install <gemname> 

# will install the name and will associate it with ruby 1.9.3

$ rvm use system --default
$ ruby -v
$ gem update --system
$ gem install <gemname> 

# will install the gemname and associate it with the default
# ruby version for your system

</pre>

**NOTE:** You will not need *sudo* when installing gems with the rvm.

# 2. pry

A replacement for the ageing *irb* (interactive ruby interpreter). Get it via gem &mdash; **gem install pry**

<pre class="codeblock">

$ rvm use 1.9.3
Using /Users/ted/.rvm/gems/ruby-1.9.3-p286
$ ruby -v
ruby 1.9.3p286 (2012-10-12 revision 37165) [x86_64-darwin12.2.0]

$ pry
[1] pry(main)> class Foo
[1] pry(main)*   def initialize(name)
[1] pry(main)*     @thename = name
[1] pry(main)*   end 
[1] pry(main)* end 
=> nil
[2] pry(main)> foo = Foo.new "Ted"
=> #<Foo:0x007febd4a83a50 @thename="Ted">
[3] pry(main)> quit

</pre>

<pre class='codeblock'>

$ irb
1.9.3p286 :001 > class Foo
1.9.3p286 :002?>   def initialize(name)
1.9.3p286 :003?>     @thename = name
1.9.3p286 :004?>     end
1.9.3p286 :005?>   end
 => nil 
1.9.3p286 :006 > foo = Foo.new "Ted"
 => #<Foo:0x007fcd83088b50 @thename="Ted"> 
1.9.3p286 :007 > 

</pre>

Pry indents better than irb, it also colorizes the code too. Color and indentation are minor stuff, pry has a lot more tricks like context switching








