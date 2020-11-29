# Troubleshooting

## Unison watch not working

#### Problem

`dockergento-apache watch` seems to do nothing

#### Reason 

Sometimes the unison watcher might not work due to problems with `inotify` in Docker.

#### Solution

Restart the docker daemon and try it again.

```
dockergento-apache watch <magento_dir>/vendor/<vendor_name>/<module_name> 
```

## (Exception): Composer file not found

#### Problem

```
Exception #0 (Exception): Composer file not found
#0 /var/www/html/site/vendor/magento/framework/Composer/ComposerFactory.php(47):
Magento\Framework\Composer\ComposerJsonFinder->findComposerJson()
```

#### Reason 

Sometimes changing git branches might break bind paths like composer file for example.

#### Solution

```
dockergento-apache restart
```
