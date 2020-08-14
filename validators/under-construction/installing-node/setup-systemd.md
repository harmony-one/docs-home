# 2. Setup Systemd



{% hint style="info" %}
Execute all the following commands  using the `root` user. On this example, we will be installing the harmony daemon for user `harmony-user` on its home directory. Daemon will be configured with the `root` user but it will run with `harmony-user`at the end.
{% endhint %}

Create the `harmony.service` file:

{% tabs %}
{% tab title="Ubuntu LTS" %}
```bash
vi /etc/systemd/system/harmony.service
```
{% endtab %}
{% endtabs %}

Add the content below to the file and save it. Change `User` to the local user you will be running the daemon and also `WorkingDirectory` to the home directory where you downloaded `node.sh` previously. Parameter `ExecStart` needs to point to this same directory.

{% tabs %}
{% tab title="Ubuntu LTS" %}
```bash
[Unit]
Description=Harmony daemon
After=network-online.target

[Service]
Type=simple
Restart=always
RestartSec=1
User=harmony-user
WorkingDirectory=/home/harmony-user
ExecStart=/home/harmony-user/node.sh -S -z
SyslogIdentifier=harmony
StandardOutput=file:/var/log/hmy.log
StandardError=file:/var/log/hmy_error.log
StartLimitInterval=0
LimitNOFILE=65536
LimitNPROC=65536

[Install]
WantedBy=multi-user.target
```
{% endtab %}
{% endtabs %}

Give the necessary permissions to run the daemon service, enable it and start it:

```bash
chmod 755 /etc/systemd/system/harmony.service
systemctl enable harmony.service
service harmony start
```

If you want to check if the daemon is running correctly you can use:

```bash
service harmony status
```

To stop the service use:

```bash
service harmony stop
```

