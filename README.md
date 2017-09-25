# relaypi
Find the scripts for the relay examples here

# install mongodb on raspbian

#Mongodb
sudo apt-get --yes --force-yes install build-essential libboost-filesystem-dev libboost-program-options-dev libboost-system-dev libboost-thread-dev scons libboost-all-dev python-pymongo git
git clone https://github.com/skrabban/mongo-nonx86
cd mongo-nonx86
scons
sudo scons --prefix=/opt/mongo install
sudo adduser --firstuid 100 --ingroup nogroup --shell /etc/false --disabled-password --gecos "" --no-create-home mongodb
mkdir /var/log/mongodb/
chown mongodb:nogroup /var/log/mongodb/
mkdir /var/lib/mongodb
chown mongodb:nogroup /var/lib/mongodb
sudo cp debian/init.d /etc/init.d/mongod
sudo cp debian/mongodb.conf /etc/
sudo ln -s /opt/mongo/bin/mongod /usr/bin/mongod
sudo ln -s /etc/init.d/mongod /etc/rc2.d/S04mongod
sudo update-rc.d mongod defaults
cd ..
