apt update 

apt install curl

curl -fsSL https://download.docker.com/linux/ubuntu/gpg |  gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg


echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" |  tee /etc/apt/sources.list.d/docker.list > /dev/null

apt update

apt-cache policy docker-ce

apt install docker-ce

systemctl status docker

apt install certbot -y

sudo certbot certonly --standalone --preferred-challenges http --agree-tos --email sobysowt@gmail.com -d parasma.clinick.online


docker build -t ocserv https://github.com/sobyf/vpn.git

docker run --name ocserv --privileged -p 443:443 -p 443:443/udp -d ocserv

Add user

docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd testUserName

Change user password

docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd testUserName

Delete user

docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -d testUserName

Lock user

docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -l testUserName

Unlock user

docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -u testUserName

Show all users and their hashed password

docker exec -ti ocserv cat /etc/ocserv/ocpasswd