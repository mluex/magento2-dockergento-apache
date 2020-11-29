# Workflow

The following guide shows you the normal development workflow using dockergento-apache.

#### 1. Start containers

```
dockergento-apache start
```
	
#### 2. Install/update dependecies with composer

```
dockergento-apache composer <install/update>
```

#### 3. Develop code normally inside `magento/app`

While developing you might need to execute magento commands like `cache:flush` for example

```
dockergento-apache magento <command>
```

#### 4. Working on frontend

```
dockergento-apache grunt exec:<theme>
dockergento-apache grunt watch
```

**NOTE:** You might also need to disable your browser cache. For example in Chrome:

* `Open inspector > Settings > Network > Disable cache (while DevTools is open)`

#### 5. Working on vendor modules [Mac only]

If you are developing code in a vendor module, you need to start unison watcher to sync files between host and container.

```
dockergento-apache watch <magento_dir>/vendor/<vendor_name>/<module_name>
```

#### 6. xdebug

* Enable xdebug

	```
	dockergento-apache debug-on
	```
		
* Configure xdebug in PHPStorm (Only first time)

	* [PHPStorm + Xdebug Setup](./xdebug_phpstorm.md)

* Sync generated **[Mac only]** 

	Because this folder is not binded for performance reasons, you need to sync it manually, so debugger finds the code in your host.

	```
	dockergento-apache mirror-container generated
	```
		
	If you edit vendor files while debugging, you have to manually transfer the files into the container
		
	```
	dockergento-apache mirror-host vendor/<subfolder_path>
	```
		
* Disable xdebug when finish 

	Environment is 10x slower when xdebug is enabled!

	```
	dockergento-apache debug-off
	```
 
#### 7. Execute tests

* All tests

	```
	dockergento-apache test-unit
	dockergento-apache test-integration
	```
	
* Only specific files

	```
	dockergento-apache test-unit <test-file-path>
	dockergento-apache test-integration <test-file-path>
	```
