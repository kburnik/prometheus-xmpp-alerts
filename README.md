# prometheus-xmpp-alerts
XMPP-Bot with Webhook for Monitoring Alerts from Prometheus (https://prometheus.io/docs/alerting/alertmanager/).

## How it works

```
|
| Alertmanager (Webhook receiver)
|
|             +------------+
+------------>| webhook.py |---+
              +------------+   |
                               |
                               | POSIX IPC MQ
                               |
              +------------+   |
+-------------| xmppbot.py |<--+
|             +------------+
|
| XMPP Messages
|
```


## Dependencies
- sudo pip3 install flask
- sudo pip3 install gunicorn
- sudo pip3 install sleekxmpp
- sudo apt-get install build-essential python-dev
- sudo pip install posix_ipc

## Start
- python3 prometheus-xmpp-alerts.py
- gunicorn -w 5 -b 127.0.0.1:8080 webhook:service
