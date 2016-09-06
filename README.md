# vsc-go-setting
Visual studio code build tasks and build/install bat and go develop plugins for golang.

## how to use

* install

	Move your GOPATH directory into visual studio code , and copy the tasks.json in .vscode directory to your .vscode directory in your GOPATH directory.Copy vscgo_build.cmd and vscgo_install.cmd to your GOPATH.

	Next , extract the package 'vsc_gotools.7z', copy all the *.exe to your %GOPATH%/bin directory , and all the go plugins are installed.

* build your project

	Now you can open any file in your project you want to build, and then use ctrl+shift+b to build your project.

* install your package

	Now you can open any file in your project you want to install, and then use ctrl+shift+p to show the command console, and enter 'tasks run task', then select the target, and choose 'vscgo_build', and your project will be installed.

* recommended

	You can set 2 GOPATH directory, put *.exe to the first one, and your project is the second one.
	And your settings.json must be <first-one>;<second-one>. This way can avoid to copy bin files in every go project.

* note

	Visual studio code may have some bugs when starting debug golang app.It doesn't pass the environment varibales in settings.json to the launch.json. And when you put the dlv to your GOPATH, vsc would't find it.

	So you need to put it in GOROOT/bin, and modify the launch.json like this:

		{
		    "version": "0.2.0",
		    "configurations": [
		        {
		            "name": "Launch",
		            "type": "go",
		            "request": "launch",
		            "mode": "debug",
		            "remotePath": "",
		            "port": 2345,
		            "host": "127.0.0.1",
		            "program": "${workspaceRoot}/src/<yourapp>",
		            "env": {"GOPATH":"${workspaceRoot}"},
		            "args": [],
		            "showLog": true
		        }
		    ]
		}