sudo useradd -m intern

sudo groupadd supervisor
sudo useradd -m smallboss
sudo useradd -m bigboss
sudo usermod -aG supervisor smallboss
sudo usermod -aG supervisor bigboss

sudo groupadd mentorship
sudo usermod -aG mentorship intern
sudo usermod -aG mentorship smallboss

touch power-point
sudo chown intern power-point
sudo chmod 644 power-point

sudo groupadd meeting
sudo usermod -aG meeting intern
sudo usermod -aG meeting smallboss
sudo usermod -aG meeting bigboss

touch token
echo '1<3L1nUx' > token
sudo chown intern:meeting token
sudo chmod 640 token

sudo gpasswd -d intern meeting
sudo gpasswd -d smallboss meeting
sudo gpasswd -d bigboss meeting
sudo groupdel meeting

chmod 744 overhead.sh
./overhead.sh

jobs -l
ps -f
