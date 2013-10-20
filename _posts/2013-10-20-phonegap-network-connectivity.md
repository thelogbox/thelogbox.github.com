---
layout: phonegap

title: Network Connectivity

description: 

excerpt: 

categories:
- phonegap

---

Your ability to detect network connectivity will be valuable. There are lots of use cases where you need to do something that depends on the device being connected or not &mdash; there are even times if you need to discriminate further whether the device wifi connected, 3g or LTE connected e.g. iOS devices don't always pull updates if the connection is less than wifi. 

To detect what kind of connectivity the device has, you need to use *navigator.connection.type* object. You will need to include the *phonegap.js* script in your code.

The connection.type object requires a plugin installation. You will have to pull some files from the Apache.org repositories.

***

Create a new project named *network* and then pull the necessary plugins.

<pre class="codeblock">

phonegap create network --name "NetworkTest" --id com.thelogbox.network

cordova plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-network-information.git

</pre>

We won't be needing anything other the *index.html* file. As usual, I've deleted the default html file created by phonegap.

{% highlight html %}

<!doctype html>

<html lang=en>
<body>

  <h1>Network exercise</h1>
  <div id="watch">
  </div>

  <script type="text/javascript" src="phonegap.js"></script>
  <script type="text/javascript" charset="utf-8">
    
  window.onload = function() {
    log("window onload");
  }  
    
  document.addEventListener("deviceready", function(){
    
    log("Device is ready");
    
    // log("Connection is : " + navigator.connection.type);
    
    var networkstate = navigator.connection.type;
    log("CONNECTION [raw] : " + networkstate);
    log("Connection constant test : " + Connection.UNKNOWN);
    
    var states = new Array();
    
    states[Connection.UNKNOWN]  = 'Unknown connection';
    states[Connection.ETHERNET] = 'Ethernet connection';
    states[Connection.WIFI]     = 'WiFi connection';
    states[Connection.CELL_2G]  = 'Cell 2G connection';
    states[Connection.CELL_3G]  = 'Cell 3G connection';
    states[Connection.CELL_4G]  = 'Cell 4G connection';
    states[Connection.CELL]     = 'Cell generic connection';
    states[Connection.NONE]     = 'No network connection';
    
    log("CONNECTION : " + states[networkstate]);
    
  },false);
  
  function log(message){
    var out = document.getElementById("watch");
    var temp = out.innerHTML;
    temp += message + "<br/>";
    out.innerHTML = temp;
  }
  
  </script>

  <style type="text/css" media="screen">
  
  * {
    font-family: Arial;
  }
  body {background: #FBFBFB;border: 1px solid #F1F1F1;}
  
  #watch {
    border: 2px solid #CACACA;
    font-size: 20px;
    background: #F1F1F1;
    padding: 5px;
  }
  </style>

</body>
</html>

{% endhighlight %}

**Compile, build and run your app.**

<pre class='codeblock'>

phonegap build ios

open platforms/ios/NetworkTest.xcodeproj

# run the simulator from within ios

</pre>
<div id='lst'>iOS build and test</div>

<pre class='codeblock'>

phonegap run android

</pre>
<div id='lst'>Android build and test</div>



<img src='/img/phonegap/network-screen.png' class='small' />
<div id='lst'>Network ConnectivityTest</div>

