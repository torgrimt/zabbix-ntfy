# zabbix-ntfy
Mediatype to add support for ntfy.sh services

Seems like noone added support for ntfy.sh into zabbix, so I spent some time to get it working myself.
Might aswell share it. Pull requests are welcome.

Download the zbx_ntfy.yaml file, go to Alerts -> Mediatypes and click import.
Change the URL field to your server and click enabled.
Fill in username and password if you run ntfy.sh behind a reverse proxy with basic authentication enabled.

Enable "Report problems to Zabbix administrators" in Alerts -> Actions -> "Trigger Actions"

Go to Users -> Users and add the ntfy.sh mediatype to your user.


