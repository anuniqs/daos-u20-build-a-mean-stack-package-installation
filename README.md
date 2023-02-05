
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
