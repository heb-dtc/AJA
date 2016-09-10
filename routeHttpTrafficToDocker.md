Route HTTP trafic to docker instance (with Apache)
Docker has been configured to map its 80 port to the host 1664 port

add new configuration file under sites-available/

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName  mydomain.com
	
	ProxyPreserveHost On
	ProxyRequests Off
	AllowEncodedSlashes NoDecode

	ProxyPass / http://localhost:1664/
	ProxyPassReverse / http://localhost:1664/

	<Proxy http://localhost:1664/>
		Order deny,allow
		Allow from all
	</Proxy>
</VirtualHost>

enable the new configuration 
sudo a2en mydomain.conf

reload apache
sudo service apache2 reload
