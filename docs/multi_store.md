# Multi Store

If you have a multi-store magento, you need to add your website codes to the Apache configuration as follows:

1. Edit `config/dockergento/apache/sites-enabled/000-default.conf`
	
```
# WEBSITES MAPPING
SetEnv MAGE_RUN_CODE base
SetEnv MAGE_RUN_TYPE website

## For multi-store configuration add here your domain-website codes
SetEnvIf Host "dominio-es.lo" MAGE_RUN_CODE=es
SetEnvIf Host "dominio-ch.lo" MAGE_RUN_CODE=ch
SetEnvIf Host "dominio-de.lo" MAGE_RUN_CODE=de
```
	
2. You need to restart dockergento-apache to apply the new configuration:
	
```
dockergento-apache restart
```
