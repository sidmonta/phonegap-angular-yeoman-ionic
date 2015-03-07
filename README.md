# phonegap-angular-yo-ionic
How to create a mobile app with Phonegap, Angular, Yeoman and Ionic


### Install all necessary
It’s assumed to have already downloaded the various tools ([Phonegap](http://phonegap.com), [Cordova](http://cordova.apache.org), [Yeoman](http://yeoman.io), [Ionic](http://ionicframework.com) e il generatore per [Angular](https://github.com/yeoman/generator-angular) ).

Create a new Phonegap project:

		phonegap create —name MyApp —id com.yourcompany.myapp myapp && cd myapp


Open the file _myapp/www/config.xml_ and add this line:

	<preference name”phonegap-version” value=“3.4.0” />

This enable phonegap to use the last version of the library.

Run the angular generator:

		yo angular [myapp]
 
Install a helful task for _grunt_:

		npm install grunt-angular-phonegap —save-dev

Now we add all platforms on which we want our application works with:

		cordova platform add [platform]

replace [platform] width _android_, _ios_, _wp7_ o _wp8_.

Now it’s time for Ionic, you install it through _bower_:

		bower install ionic —save-dev

### Structure of the project

Add all plugin of _Phonegap_ that interest us.

	1.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-device.git 

	2.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-network-information.git 

	3.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-battery-status.git

	4.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-dialogs.git

	5.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-vibration.git

	6.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-splashscreen.git


Add the reference to cordova:

		<script src=“cordova.js”></script>

in the file _index.html_

If bower didn’t add in automatic the reference of Ionic, do ourself.

Another change to think to do is update the target of Android in  _AndroidManifest_.

### How to run it

First run the grunt server:

		grunt serve

For build the app for a specific platform use the grunt task previously installed:

		grunt phonegap:build:platform

meanwhile for run the emulator use ionic:

		ionic emulate platform

### Debug and Test

The debug is possible, for iOS, by _Safari_ width the _Developers tool_.
For the test in device look the reference of the Ionic App [here](http://apps.ionic.io/apps)