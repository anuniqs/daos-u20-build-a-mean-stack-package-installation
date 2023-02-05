
## Set Up a Node.js Application for Production,

### Server preconfiguration,

`anup@u22-128-YT-MACHINE:~$ sudo su -`

`anup@u22-128-YT-MACHINE:~$ nano /etc/ssh/sshd_config`

    PermitRootLogin yes
    PubkeyAuthentication yes

`root@u22-128-YT-MACHINE:~# nano /etc/hosts`

    192.168.56.128  u22-128-YT-MACHINE

`root@u22-128-YT-MACHINE:~# apt update -y`

`root@u22-128-YT-MACHINE:~# apt list --upgradable`

`root@u22-128-YT-MACHINE:~# apt upgrade -y`

<br>


### Install MongoDB,

https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/

`root@u22-128-YT-MACHINE:~# apt install python3 dirmngr gnupg apt-transport-https ca-certificates software-properties-common -y`

`root@u22-128-YT-MACHINE:~# wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | apt-key add -`

`root@u22-128-YT-MACHINE:~# echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.4.list`

<br>

`root@u22-128-YT-MACHINE:~# wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2_amd64.deb`

`root@u22-128-YT-MACHINE:~# dpkg -i libssl1.1_1.1.1f-1ubuntu2_amd64.deb`

<br>

`root@u22-128-YT-MACHINE:~# apt-get update -y`

`root@u22-128-YT-MACHINE:~# apt-get install mongodb-org -y`

<br>

`root@u22-128-YT-MACHINE:~# systemctl start mongod`

`root@u22-128-YT-MACHINE:~# systemctl enable mongod`

`root@u22-128-YT-MACHINE:~# systemctl status mongod`

<br>


### Install Node.js,

https://nodejs.org/en/

https://nodejs.org/en/download/

https://nodejs.org/en/download/package-manager/

https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions

https://github.com/nodesource/distributions/blob/master/README.md

<br>

`root@u22-128-YT-MACHINE:~# apt-get install curl`

`root@u22-128-YT-MACHINE:~# curl -sL https://deb.nodesource.com/setup_18.x | bash -`

`root@u22-128-YT-MACHINE:~# apt-get install nodejs -y`

<br>

`root@u22-128-YT-MACHINE:~# node -v`

`root@u22-128-YT-MACHINE:~# npm -v`

<br>

`root@u22-128-YT-MACHINE:~# npm install -g yarn`

`root@u22-128-YT-MACHINE:~# yarn -v`

<br>

`root@u22-128-YT-MACHINE:~# npm install -g gulp`

`root@u22-128-YT-MACHINE:~# gulp -v`

<br>

`root@u22-128-YT-MACHINE:~# npm install pm2 -g`

`root@u22-128-YT-MACHINE:~# pm2 -v`

<br>


### Install Python and Git,

`root@u22-128-YT-MACHINE:~# apt-get install python2.7`

`root@u22-128-YT-MACHINE:~# ln -s /usr/bin/python2.7 /usr/bin/python`

`root@u22-128-YT-MACHINE:~# python --version`

`root@u22-128-YT-MACHINE:~# python3 --version`

<br>

`root@u22-128-YT-MACHINE:~# apt-get install git`

<br>


### Download , Install and Configure MEAN Stack,

`root@u22-128-YT-MACHINE:~# git clone https://github.com/meanjs/mean`

`root@u22-128-YT-MACHINE:~# cd mean`

`root@u22-128-YT-MACHINE:~/mean# yarn install`
