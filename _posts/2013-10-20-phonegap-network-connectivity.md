---
layout: phonegap

title: Network Connectivity

description: How to detect if the device has internet connection

excerpt: 

author: Ted Hagos

lastupdate: 2013-11-08

tags:
- Network
- Connectivity
- Plugin

---

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

Your ability to detect network connectivity will be valuable. There are lots of use cases where you need to do something that depends on the device being connected or not &mdash; there are even times if you need to discriminate further whether the device wifi connected, 3g or LTE connected e.g. iOS devices don't always pull updates if the connection is less than wifi. 

To detect what kind of connectivity the device has, you need to use **navigator.connection.type** object. You will need to include the **phonegap.js** script in your code.

The **connection.type** object requires a plugin installation. You will have to pull some files from the Apache.org repositories.



Create a new project. For the purpose of this exercise, the project name will be **network**.


~~~
$ phonegap create network --name "NetworkTest" --id com.thelogbox.network
~~~

Next, we will get the necessary plugins.

~~~
$ cordova plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-network-information.git
~~~


We won't be needing anything other the **index.html** file. I have deleted the default html file created by phonegap and replaced it with the one below.

~~~
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

~~~

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

The following command will build and run your app

~~~
$ phonegap build ios
$ open platforms/ios/NetworkTest.xcodeproj
~~~

That last command will launch **XCode**. You can then run your app within XCode.

To run the android emulator, use the following command

~~~
phonegap run android
~~~


<img src='/img/phonegap/network-screen.png' class='small' />


<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>
