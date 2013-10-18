---
layout: androidtutorial

title: Creating a Project in Eclipse

description:

except:

categories:
- android-programming

---


## What you need to proceed
1. [A properly installed Android SDK](/installing-android-sdk/)
2. [Properly installed Eclipse plugin for Android](/android-install-eclipse-plugin/)

## Create a basic Activity based android project in Eclipse

From the Eclipse menu, choose **New project**. Select *Android*, drill down to **Android Application Project**, Click Next.

<img src="/img/eclipse-new-project-1.png">

Eclipse will ask for some information about the project

- **Application name** - This is the top level folder that will be created, it will become the root folder of the project. This is equivalent to the *--path* flag of the **android create project**

- **Project name** - The project name is an eclipse construct. Eclipse uses this information to identify the project within the Eclipse workspace

- **Package name** - The Java source files will be stored using the package directive that we specify in the option. The package directive will only affect the location of Java source files, it will not affect the location and storage of the other android resources (i.e. XML files). This is the exact equivalent of the *--package* directive in the **android create project**

- **Build SDK** - This value stands for a unique API level for a specific android version which you want the project to target. This is the equivalent of the *--target* directive in the **android create project**

- **Minimum required SDK** - it sets the minimum API level or android version on which the project can run on. This value gets inserted in the AndroidManifest.xml file

<img src="/img/eclipse-new-project-2.png">

If you clicked the *launcher icon* option, Eclipse will show a dialog where you can create a rudimentary icon for hte application.

<img src="/img/eclipse-new-project-3.png">

Choose *BlankActivity*. The *MasterDetailFlow* option is pretty advanced stuff---also, it requires a higher SDK level. It won't be available for Froyo or Gingerbread.

<img src="/img/eclipse-new-project-4.png">

**Activity Name** will be the name of main (Activity class). This is the equivalent of the *--activity* directive on the **android create project**.

The **Layout Name** will be the name of the XML file which will contain the instructions for the main UI. This is the equivalent of the file *android-project-folder/res/layout/main.xml*


<img src="/img/eclipse-new-project-5.png">




