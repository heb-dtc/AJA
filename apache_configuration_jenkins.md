# Basic Apache Configuration on MacOs X

To expose Jenkins on the  network and make it possible for ```Gitlab``` to reach it we need to use a web server.

```Apache2``` is pre-installed on MacOS so one solution is to configure a ```VHOST``` and to use a reverse proxy to route  all connections on the port **80** to the ```Jenkins``` instance running on the port **8080**.

Apache2 basics
==== 

To start apache from command line 
```
$ sudo apachectl start
```

To stop apache from command line
```
$ sudo apachectl stop
```

To restart apache after configuration change
```
$ sudo apachactl -k restart
```

To check if the configuration is valid
```
$ sudo apachectl configtest
```
> after each configuration change, the apache server NEEDS to be restarted

Apache configuration files are located under
```
/etc/apache2/httpd.conf
/etc/apache2/extra/httpd-vhosts.conf
```

Vhost management
===

First thing is to enable the ```vhost``` in apache configuration file

1. Open httpd.conf
```
$ sudo vim /etc/apache2/httpd.conf
```
2. look for the line that include the vhost configuration file and uncomment it (remove the **#** in front)
```
Include /private/etc/apache2/extra/httpd-vhosts.conf
```
3. look for the line that loads the vhost alias module and uncomment it
```
LoadModule vhost_alias_module libexec/apache2/mod_vhost_alias.so
```  

Second thing is to create the ```vhost``` to expose the ```Jenkins``` instance

1. open the vhost configuration file
```
sudo vim /etc/apache2/extra/httpd-vhosts.conf
```
2. add the vhost configuration
```
<VirtualHost *:80>
    ProxyPreserveHost On
    #ProxyRequests Off
    #AllowEncodedSlashes NoDecode
   
    ProxyPass / http://localhost:8080/ nocanon
    ProxyPassReverse / http://localhost:8080/

    <Location /jenkins/>
        ProxyPassReverse /
        Order deny,allow
        Allow from all
    </Location>
</VirtualHost>
```
  

Finally, enable properly the reverse proxy modules of apache

using the a2enmod command
```
a2enmod proxy
a2enmod proxy_http
a2enmod headers
```
or by uncommenting the lines directly in apache config file
```
LoadModule headers_module libexec/apache2/mod_headers.so
LoadModule proxy_html_module libexec/apache2/mod_proxy_html.so
LoadModule proxy_module libexec/apache2/mod_proxy.so
```
