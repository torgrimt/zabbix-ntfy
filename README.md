# zabbix-ntfy (v1.0.0)
Mediatype to add support for [ntfy.sh](https://ntfy.sh/) notifications in [Zabbix](https://www.zabbix.com/).

## Setup
1. Download the `zbx_ntfy.yaml` file.
2. Go to **Alerts -> Media types** and click **Import**.
![Media Types](./docs/img/media_types.png)

### Configuration (Global Macros)
Go to **Administration -> Macros** and create the following macros to define your ntfy instance:
![Macros](./docs/img/macros.png)

| Macro | Description | Requirement |
| :--- | :--- | :--- |
| `{$NTFY.URL}` | The URL to your ntfy instance (e.g., `https://ntfy.sh`). | **Required** |
| `{$NTFY.SENDTO}` | Global topic name for all alerts. | Optional |
| `{$NTFY.TOKEN}` | Auth token for ntfy (Bearer). | Optional |
| `{$ZABBIX.URL}` | URL to your Zabbix (e.g., `https://zabbix.example.com`). | Optional |

### User Settings
Go to **Users -> Users**, select a user, and navigate to the **Media** tab.
1. Add the **ntfy.sh** media type.
2. The **Send to** field must be populated. If you use the global topic macro, just enter `dummy`.
![User Media](./docs/img/user_media.png)

## Troubleshooting
If notifications are not arriving, check the Zabbix Server logs (usually `/var/log/zabbix/zabbix_server.log`).

| Error Message | Possible Cause |
| :--- | :--- |
| `Cannot get ntfy url!` | The macro `{$NTFY.URL}` is missing or empty. |
| `Nseverity value must be passed as an int` | Internal Zabbix error where severity mapping failed. |
| `Sending failed: HTTP/1.1 401 Unauthorized` | Invalid Token or Username/Password. |
| `Sending failed: HTTP/1.1 404 Not Found` | The Topic name or ntfy URL is incorrect. |

## Customization
Priorities are mapped from Zabbix Severities to ntfy priorities (min, low, default, high, urgent). To change these, edit the Media Type parameters in Zabbix.
