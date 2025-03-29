# traccar-raspberrypi
Install raspbian lite using the Raspberry Pi installer.

sudo su
apt install default-jre
mkdir /opt/traccar
cd /opt/traccar

Download latest version of traccar from https://www.traccar.org/download/
wget https://github.com/traccar/traccar/releases/download/v6.6/traccar-linux-arm-6.6.zip
unzip traccar-linux-arm-6.6.zip
./traccar.run

