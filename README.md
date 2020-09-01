# traccar-config-centos-7

"/etc/httpd/conf/httpd.conf"
allowoveride all

"/etc/httpd/conf.d/traccar.conf"
Traccar in subdirectory (non root path)
If you want Traccar to be in a subdirectory, you also need to adjust cookies path. Here is a proxy configuration example:

ProxyRequests off

ProxyPass /gps/api/socket ws://localhost:8082/api/socket
ProxyPassReverse /gps/api/socket ws://localhost:8082/api/socket

ProxyPass /gps/ http://localhost:8082/
ProxyPassReverse /gps/ http://localhost:8082/
ProxyPassReverseCookiePath / /gps/

Redirect permanent /gps /gps/
