

## Stand alone server

The Liberty Profile runtime  can be downloaded as a **jar** file. If you plan to build Web Services or use JMS or perhaps use a MongoDB backend for your applications, you also need to download the Liberty Profile Extended Content, which is also packaged as a jar file. The Liberty Profile Runtime and the Extended Content jar files can be downloaded at [developer.ibm.com site](https://developer.ibm.com/wasdev/downloads/liberty-profile-using-non-eclipse-environments/). Once you click the download link for the runtime and the extended content jars, you will be asked to accept the license agreement. If you agree, the download process will begin.

Choose an appropriate directory where you want to install the Liberty Profile runtime. It is best to install the Liberty runtime in a directory where you will not need any admnistrator or root privileges. For purposes of development, it is suggested to install the runtime on your home directory. The table below shows the user directories, depending on what OS you are using.

|         | DIRECTORY             |
|-------------------------------- |
| Windows | C:\Users\yourUsername |
| OSX     | /Users/yourUsername   |
| Linux   | /home/yourUsername    |

Copy the jar files somewhere in your user directory and run them.

~~~

java -jar wlp-developers-runtime-8.5.5.3.jar

~~~

The installer is text based. It will ask you to accept the license agreement. Type **x** when prompted to skip reading the license agreement, or you may read it if you want to. Follow the prompts and accept the agreement. You may have to type **1** to signify that you accept the agreement. Finally, it will ask where you want to install the wlp, short for WebSphere Liberty Profile, the default directory is the current directory. Just press **RET** to accept the default.

If you need the Extended Content runtime, run the installer

~~~
jar -jar wlp-developers-extended-8.5.5.3.jar
~~~

Same steps will apply when you intalled wlp, as described above. Just accept the default location so that it installs on the same folder as the runtime.




