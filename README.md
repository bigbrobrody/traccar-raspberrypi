# traccar-raspberrypi
Install raspbian lite using the Raspberry Pi installer.  
Then:

```
sudo su
apt install default-jre
mkdir /opt/traccar
cd /opt/traccar
```

Download latest version of traccar from https://www.traccar.org/download/

```
wget https://github.com/traccar/traccar/releases/download/v6.6/traccar-linux-arm-6.6.zip
unzip traccar-linux-arm-6.6.zip
./traccar.run
```

`nano /etc/systemd/system/traccar.service`  
And remove /opt/traccar/jre/bin/java from before java  

```
adduser traccar
chown -R traccar:root /opt/traccar
mkdir /etc/systemd/system/traccar.service.d/
touch /etc/systemd/system/traccar.service.d/run-as-user.conf
```

`nano /etc/systemd/system/traccar.service.d/run-as-user.conf`  
And add:  
```
[Service]
User=traccar
Group=traccar
```

```
systemctl daemon-reload
systemctl restart traccar.service
systemctl status traccar.service
tail -f -n 300 /opt/traccar/logs/tracker-server.log
```

The traccar web page should then be available on port 8082 on the IP address of the Raspberry Pi.  
Ports used by trackers will need to be forwarded to the Raspberry Pi.
