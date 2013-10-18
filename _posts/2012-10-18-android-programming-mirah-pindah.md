---
layout: androidtutorial

title: Mirah and Pindah

description:

except:

categories:
- andorid-programming

---


Mirah is a relatively young language (v.08 when I got wind of it, and at the time of writing). It compiles to Java (it emits Java code), it has no runtime library and its syntax is borrowed from Ruby. See [official Mirah site](http://www.mirah.org) for more info about the language.

To use Mirah for Android programming, we will tap another tool to handle the android project creations and build mechanism &mdash; we will use [pindah](https://github.com/mirah/pindah). Pindah works great as a replacement for the *android create project  ...* CLI, it is also a great replacement for the *ant* build scripts, it uses *rake* 


# SETUP



1. Get ruby and rubygems
2. Get RVM (Ruby Version Manager)
3. Get JRuby &mdash; *rvm install jruby*
4. Get mirah &mdash; *gem install mirah*
5. Get pindah &mdash; *gem install pindah*
6. Make sure you have a really good source code editor
7. Brush up on Ruby, because mirah's syntax is ruby, just keep in mind that mirah is not ruby, it just looks and feel a lot like it
8. Brush up on the android SDK and API, best source of information on the APIs is [developer.android.com](http://developer.android.com/develop/index.html). There are lots of tutorials you can follow on Android development.


# EVENT HANDLING AND NOTIFICATION


1. *pindah create com.thelogbox toastcode ToastCode* to create the project
2. cd toastcode
3. **android update project -p . &mdash;target 8** to set the target API to level 8 (Froyo)
4. **pindah** will produce exactly the same project layout as would *android create project*, so go the *src* folder and work on the generated *ToastCode.mirah* source file
5. Connect and android device (preferred) or create an AVD to emulate an physical device (really slow)
6. **pindah** generated a rake file, so use it **rake debug install**; use the debug option of rake so you won't have to deal with signing the .apk before you can test the code

{% highlight ruby %}

package com.thelogbox

import android.app.Activity
import android.os.Bundle
import android.widget.Toast
import android.content.Context
import android.view.View
import android.widget.LinearLayout
import android.widget.Button


class ToastView < LinearLayout
    
  def initialize(ctx:Context)
    super(ctx)
    
    @ctx = ctx
    @button = Button.new ctx 
    
    @button.setText "Toast me!"
    @button.setOnClickListener do |x|
      notification = Toast.makeText(ToastCode.ctx, "Yo", Toast.LENGTH_SHORT)
      notification.show()
    end
       
    setOrientation(LinearLayout.VERTICAL)
    addView(@button)
  end
    
end

class ToastCode < Activity

  def onCreate(state)
    super state    
    @view = ToastView.new self
    @@ctx = getApplicationContext()
    
    setContentView @view
  end
  
  def self.ctx
    @@ctx
  end
end

{% endhighlight %}

The generated **R.layout.main** is completely ignored by this code, the UI is defined entirely in this single source file. The LinearLayout class is a descendant of android.view.View, which means you set the content view of an Activity class to an instance of a custom LinearLayout, hence the class **ToastCode** extending the LinearLayout class.

To handle the onClick of the button, usually you will need an **OnClickListener**
object. This is usually accomplished using an anonymous class. In the sample code, the callback function was achieved using a code block

{% highlight ruby %}

# ANONYMOUS METHOD

@button = Button.new context
@button.setOnClickListener do |x|
  # code here ...
end
{% endhighlight %}

This is good if the code you need to write during click events are short. If the functionality gets a bit more involved, setting up proper *OnClickListener* objects might be a cleaner approach

To setup OnClickListeners, just implement the View.OnClickListener interface in the View class (LinearLayout is subclass of View)

{% highlight ruby %}

# handling click event using OnClickListener

import android.view.View
import android.content.Context
import android.widget.LinearLayout
import android.widget.Button
import android.view.ViewGroup
import android.view.View.OnClickListener
import android.widget.LinearLayout.LayoutParams
import android.view.View.OnClickListener


class ToastView < LinearLayout
  implements OnClickListener
  
  def initialize(ctx:Context)
    super ctx
    
    @btnsave = Button.new ctx       
    @btnsave.setLayoutParams getLayoutParams    
    @btnsave.setText "Save"    
    @btnsave.setOnClickListener(self)
    
    # ADD the widgets to the MainView
    
    addView @btnsave
    setOrientation LinearLayout.VERTICAL    
  end
  
  def getLayoutParams:LayoutParams
    width = ViewGroup.LayoutParams.FILL_PARENT
    height = ViewGroup.LayoutParams.WRAP_CONTENT    
    LayoutParams.new width, height
  end
  
  def onClick(view:View)
    # ... code when button is clicked
  end
    
end

{% endhighlight %}

# DETECTING EVENT SOURCE


{% highlight ruby %}

package com.thelogbox

import android.app.Activity
import android.widget.LinearLayout
import android.widget.Button
import android.content.Context
import android.view.View
import android.view.View.OnClickListener
import android.widget.Toast

class ButtonsView < LinearLayout
  implements OnClickListener
  
  def initialize(ctx:Context)
    super ctx
    
    @one = Button.new ctx
    @two = Button.new ctx
    @three = Button.new ctx
    
    @one.setText "One"
    @two.setText "Two"
    @three.setText "Three"
    
    # need to set the Id  of each Button obj because this is
    # is what we will use to determine which of them was clicked
    
    @one.setId 1
    @two.setId 2
    @three.setId 3
    
    @one.setOnClickListener self
    @two.setOnClickListener self
    @three.setOnClickListener self

    addView(@one)
    addView(@two)
    addView(@three)
    
    setOrientation LinearLayout.VERTICAL

  end
  
  def onClick(v:View)
    
    # v.getId will return an integer. If you defined the view declaratively, the AAPT
    # (android asset packaging tool) would have kicked in and generated an R.layout.xxx
    # java class, we could use that id to determine which button was clicked.
    # But since the view was done programmatically, the aapt did not kick in, hence
    # we need to define our own ids for each button
    
    toast = Toast.makeText(Buttons.getAppContext,"#{v.getId}", Toast.LENGTH_SHORT)
    toast.show
  end
  
end

class Buttons < Activity
  def onCreate(state)
    super state
    @@ctx = getApplicationContext
    setContentView ButtonsView.new(self)
  end
  
  def self.getAppContext
    @@ctx
  end
  
end

{% endhighlight %}










