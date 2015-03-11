# phonegap-angular-yo-ionic
How to create a mobile app with Phonegap, Angular, Yeoman and Ionic


### Required install
It’s assumed to have already downloaded all the tools ([Phonegap](http://phonegap.com), [Cordova](http://cordova.apache.org), [Yeoman](http://yeoman.io), [Ionic](http://ionicframework.com) and the [Angular](https://github.com/yeoman/generator-angular) generator ).

Create a new Phonegap project:

		phonegap create —name MyApp —id com.yourcompany.myapp myapp && cd myapp


Open the file _myapp/www/config.xml_ and add this line:

	<preference name”phonegap-version” value=“3.4.0” />

This enable phonegap to use the last version of the library.

Run the angular generator:

		yo angular [myapp]
 
Install a helpful task for _grunt_:

		npm install grunt-angular-phonegap —save-dev

Now add all platforms on which we want our application to works with:

		cordova platform add [platform]

replace [platform] width _android_, _ios_, _wp7_ o _wp8_.

Now it’s time for Ionic, install it through _bower_:

		bower install ionic —save-dev

### Structure of the project

Add all the required plugin of _Phonegap_.

	1.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-device.git 

	2.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-network-information.git 

	3.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-battery-status.git

	4.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-dialogs.git

	5.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-vibration.git

	6.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-splashscreen.git


Add the cordova reference:

		<script src=“cordova.js”></script>

in the file _index.html_

If bower it’s unable add the Ionic references, be sure to add it 

Another think to do is update the target of Android in  _AndroidManifest_.

Another thing we can do it’s modify the target of Android application in _AndroidMonifest_. 

### How to run it

First run the grunt server:

		grunt serve

To build the app for a specific platform use the grunt task previously installed:

		grunt phonegap:build:platform

meanwhile to run the emulator use ionic:

		ionic emulate platform

### Debug and Test

The debug is possible for iOS, using _Safari_ by opening the  _Developers tool_.
For the test in device look the references of the Ionic App [here](http://apps.ionic.io/apps)