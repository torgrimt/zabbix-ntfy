# zabbix-ntfy
Mediatype to add support for ntfy.sh services

Seems like no one added support for [ntfy](https://ntfy.sh/) into [Zabbix](https://www.zabbix.com/) server, so I spent some time to get it working myself. Might as well share it. Pull requests are welcome.

## Setup
Download the `zbx_ntfy.yaml` file, go to *Alerts -> Mediatypes* and click **Import**.

Go to: *Administration -> Macros* and create Macros:
- `{$NTFY.URL}` The URL to send ntfy requests to. Just `https://ntfy.sh` if using the main instance.
- `{$NTFY.SENDTO}` The ntfy topic to send the request to.
- `{$ZABBIX.URL}` The URL to your Zabbix instance to include a clickable link in the notification (optional).
- `{$NTFY.USER}` The username of the ntfy account to use (optional - basic authentication).
- `{$NTFY.PASS}` The password of the ntfy account to use (optional - basic authentication).
- `{$NTFY.TOKEN}` The token created for the ntfy account to use (optional - token authentication).

Enable a trigger action to use the NTFY Media Type: *Alerts -> Actions -> Trigger Actions*.

Go to *Users -> Users* and add the ntfy.sh Media Type to your user. The *Send To* field needs to be populated, but isn't used for anything.

## Customization
### Message Priority
Priorities are, by default, based on the Zabbix Triggers priority. To adjust the levels, go to *Alerts -> Media Types -> ntfy.sh* and adjust the `Priority_*` parameters to your liking. These options match the [NTFY API](https://docs.ntfy.sh/publish/#message-priority).

### Topic
The topic to send the request to can be set globally or per user.
#### Global
This is the default. Set the global macro `{$NTFY.SENDTO}` to the topic that should be used for all users. Users can not configure individual topics.
#### Per User
The golbal macro `{$NTFY.SENDTO}` is not needed. The macro `{ALERT.SENDTO}` is used instead.

Global steps to enable:
1. Navigate to Administration --> Media Types --> ntfy.sh --> Parameters
2. Change `Topic` to `{ALERT.SENDTO}`
3. Click `Update`

User steps to enable:
1. Navigate to User settings --> Profile --> Media --> Edit ntfy.sh
2. Set `Send To` to the topic to be used for this user
3. Click `Update` in the popup
4. Click `Update` below the List again

## Also
For more information and discussion, see:
- [ntfy integration documentation](https://docs.ntfy.sh/integrations/#projects-scripts)
- [Zabbix Forum post](https://www.zabbix.com/forum/zabbix-cookbook/475107-how-to-add-the-ntfy-sh-notification-service-as-media-type-in-zabbix)
