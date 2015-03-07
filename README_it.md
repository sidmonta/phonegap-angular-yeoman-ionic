# Phonegap-Angular-Yeoman-Ionic
Come creare una applicazione mobile con Phonegap + AngularJS + Yeoman + Ionic

### Installare il necessario
Si assume di aver già scaricato i vari tool ([Phonegap](http://phonegap.com), [Cordova](http://cordova.apache.org), [Yeoman](http://yeoman.io), [Ionic](http://ionicframework.com) e il generatore per [Angular](https://github.com/yeoman/generator-angular) ).

Si procede a creare un nuovo progetto Phonegap:

		phonegap create —name MyApp —id com.yourcompany.myapp myapp && cd myapp


Si apre il file _myapp/www/config.xml_ e si dice di usare l’ultima libreria di phonegap, lo si fa aggiungendo la seguente riga:

		<preference name”phonegap-version” value=“3.4.0” />

Avviare il generatore di Angular

		yo angular [myapp]

Installare un task utile per _grunt_:

		npm install grunt-angular-phonegap —save-dev

Aggiungiamo tutte le piattaforme sulla quale vogliamo che la nostra applicazione funzioni con:

	cordova platform add [platform]

sostituendo [platform] con _android_, _ios_, _wp7_ o _wp8_.

Ora tocca a Ionic, lo si installa attraverso _bower_ con:

		bower install ionic —save-dev


### Ora si passa alla strutturazione del progetto.

Si aggiungono tutti i plugin di _Phonegap_ che interessano:

	1.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-device.git 

	2.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-network-information.git 

	3.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-battery-status.git

	4.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-dialogs.git

	5.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-vibration.git

	6.			phonegap local plugin add https://git-wip-us.apache.org/repos/asf/cordova-plugin-splashscreen.git


Passiamo alla modifica del progetto.

Per prima cosa dobbiamo aggiungere la libreria di cordova:

		<script src=“cordova.js”></script>

nel file _index.hmtl_.
Qualora bower non abbia aggiunto in automatico il riferimento alla libreria di ionic, provvediamo noi stessi.

Un’altra modifica che si può pensare di fare è quella di andate a modificare il target della piattaforma android nell’apposito _AndroidManifest_.

### Come eseguire

Per prima cosa, come al solito si consiglia di attivare il server grunt:

		grunt serve

Per compilare il progetto per una specifica piattaforma si utilizza il task di grunt precedentemente installato:

		grunt phonegap:build:platform

mentre per lanciare l’emulazione dell’applicazione:

		ionic emulate platform

### Debug e Test

Il debug lo si può fare, per iOS, attraverso _Safari_ attraverso il menu _Sviluppo_.
Per il test su dispositivi reali si guardi i riferimenti all’applicazione messa a disposizione dal team di Ionic [qui](http://apps.ionic.io/apps)