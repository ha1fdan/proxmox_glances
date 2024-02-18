# Monitor Proxmox with Glances

1. `rm -rf /usr/lib/python3.*/EXTERNALLY-MANAGED`
2. `curl -L https://raw.githubusercontent.com/nicolargo/glancesautoinstall/master/install.sh | /bin/bash`
3. `echo "drivetemp" >> /etc/modules`
4. `modprobe drivetemp`
5. `nano /etc/systemd/system/glances.service`
```
[Unit]
Description=Glances
After=network.target

[Service]
ExecStart=/usr/local/bin/glances -w
Restart=on-abort
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```
6. `systemctl enable glances.service`
7. `systemctl start glances.service`
8. http://server-ip:61208/
