+++
title = "Ionic Framework"
date = 2017-11-21
weight = 600
tags = ["Ionic", "WebApp"]
+++

{% include toc %}

# Ionic
Ionic is a complete open-source SDK for hybrid mobile app development built on top of AngularJS and Apache Cordova. this helps developing hybrid mobile apps using Web technologies like CSS, HTML5, and Sass.

# Cons & Pros
The purpose of using Ionic is that I can deploy both Android and IOS; furthermore even web, within same code.
So it would save my time to develop apps. However, generally, people say that this is bit slower than native apps.


# Type
Ionic supports two types: `Ionic1` and `Ionic2`. <br>
Ionic 1 based on Angular 1 where Ionic 2 based on Angular 2
<!--
The advantage of Ionic 1:

	More classic than Ionic 1.
	Older than Ionic 2, so bit more stable.
-->

The advantage of Ionic 2 over Ionic 1 is:

	Angular 2 is faster
	Angular2 use components instead of controller (developer feels simpler)
	Angular2 has simpler directive
	intuitive data binding

# Requirements

- download **ionic**: <br>
	[http://ionicframework.com/docs/overview/#download](http://ionicframework.com/docs/overview/#download "http://ionicframework.com/docs/overview/#download")

- download **nodejs**: <br>
	[https://nodejs.org/en/download/](https://nodejs.org/en/download/ "https://nodejs.org/en/download/")

- download **cordiva** npm package: (to support multi-platform)<br>  

		npm install -g cordova

- download **gulp** npm package: (ionic's build system)<br>

		npm install -g gulp

- download **bower** npm package: (to bring web components)<br>

		npm install -g bower

- For a simulation,<br>
  download **ios-sim**: (for an ios simulation) <br>

		npm install -g ios-sim

- download **ios-deploy**: (for installation or debugging) <br>

	 	npm install -g ios-deploy

		if this is unable to install, try this:
			sudo npm install -g ios-deploy --unsafe-perm=true

First of all, tried OS X (Yosemite) installation on virtual machine, but was unstable (hang while booting and etc). Therefore, for second, "El Capitan" was installed; however, after few hours of using it, it has been realized that running both Android and IOS on OS X on top of virtual machine is difficult. Therefore, it is recommended to have Macbook pro for mobile and web development.   

# El Capitan Installation reference for Virtual box

To give you a guide to install "El Capitan", please refer to below.

English    
> https://techsviewer.com/how-to-install-mac-os-x-el-capitan-on-pc-on-virtualbox/

Korean
> http://weixing.tistory.com/289

on the OS, you must have followings (need to be installed using npm):

- brew
- nodejs

# Full Screen for OS X

If you do not see OS in Full screen, try below:

	VBoxManage setextradata "VM name" VBoxInternal2/EfiGopMode N
    Where N can be,

	0 – 640×480
	1 – 800×600
	2 – 1024×768
	3 – 1280×1024
	4 – 1440×900
	5 – 1920×1200

Or,

	VBoxManage setextradata "El Capitan" CustomVideoMode1 1920x1080x32

## XCode Installation Issue

Issue related to "**Simulator can't be opened**":
Click [Here](http://stackoverflow.com/questions/33413180/xcode-7-1-simulator-cant-be-opened-because-the-identity-of-developer-cannot-b)


## Test Ionic

1. `sudo ionic run ios --device`

2. Select a target: `ionic emulate ios --target="iPhone-4s"`

3. Change mode of directory to run the Ionic file: `sudo chmod -R 777 *`


## Reference:
http://blog.saltfactory.net/ionic/start-ionic-edge-book.html (Korean)


#Troubleshooting

Installing npm using,

	npm install -g ionic cordova

could return following erros:

	53840 warn In ionic@2.0.0 replacing bundled version of semver with semver@4.2.0
	53841 warn In ionic@2.0.0 replacing bundled version of ionic-app-lib with ionic-app-lib@2.0.0
	53842 verbose stack Error: ENOENT: no such file or directory, rename '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/.staging/ansi-93ed635c' -> '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/ionic/node_modules/cordova-lib/node_modules/ansi'
	53842 verbose stack     at destStatted (/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/npm/lib/install/action/finalize.js:25:7)
	53842 verbose stack     at FSReqWrap.oncomplete (fs.js:82:15)
	53842 verbose stack
	53842 verbose stack Error: ENOENT: no such file or directory, rename '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/.staging/ansi-93ed635c' -> '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/ionic/node_modules/cordova-lib/node_modules/ansi'
	53842 verbose stack     at Error (native)
	53843 verbose cwd /dev.snaphappi.com/_ng2/mappi0
	53844 error Darwin 15.6.0
	53845 error argv "/Users/m/.nvm/versions/node/v5.12.0/bin/node" "/Users/m/.nvm/versions/node/v5.12.0/bin/npm" "install" "-g" "ionic"
	53846 error node v5.12.0
	53847 error npm  v3.8.6
	53848 error path /Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/.staging/ansi-93ed635c
	53849 error code ENOENT
	53850 error errno -2
	53851 error syscall rename
	53852 error enoent ENOENT: no such file or directory, rename '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/.staging/ansi-93ed635c' -> '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/ionic/node_modules/cordova-lib/node_modules/ansi'
	53853 error enoent ENOENT: no such file or directory, rename '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/.staging/ansi-93ed635c' -> '/Users/m/.nvm/versions/node/v5.12.0/lib/node_modules/ionic/node_modules/cordova-lib/node_modules/ansi'
	53853 error enoent This is most likely not a problem with npm itself
	53853 error enoent and is related to npm not being able to find a file.
	53854 verbose exit [ -2, true ]

This could be due to re-installation of ionic, in this case,<br>
remove the installation and do reinstallation

	npm -g remove ionic
	npm install -g ionic cordova

## Run Ionic
To run ionic in Windows command prompt, execute this first:

	"C:\Program Files\nodejs\nodevars.bat"
