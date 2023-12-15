# zabbix-ntfy
Mediatype to add support for ntfy.sh services

Seems like noone added support for ntfy.sh into zabbix, so I spent some time to get it working myself.
Might aswell share it. Pull requests are welcome.

Download the zbx_ntfy.yaml file, go to Alerts -> Mediatypes and click import.
You need to create macros with ntfy url, optional username and password.
Go to: Administration -> macros. Here you need to create those 3 macros named
NTFY.URL
NTFY.USER
NTFY.PASS

Username and password is if you use basic auth. Should work without them if you dont have it.

Enable "Report problems to Zabbix administrators" in Alerts -> Actions -> "Trigger Actions"

Go to Users -> Users and add the ntfy.sh mediatype to your user.


