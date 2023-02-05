
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

<br>


### Create MEAN Application,

`root@u22-128-YT-MACHINE:~/mean# nano server.js`

    const express = require('express');
    const MongoClient = require('mongodb').MongoClient;
    const app = express();
    
    app.use('/', (req, res) => {
    MongoClient.connect("mongodb://localhost:27017/test", function(err, db){
    db.collection('Example', function(err, collection){
    collection.insert({ pageHits: 'pageHits' });
    db.collection('Example').count(function(err, count){
    if(err) throw err;
    res.status(200).send('Page Hits: ' + Math.floor(count/2));
    });
    });
    });
    });
    
    app.listen(3000);
    console.log('Server running at http://localhost:3000/');
    
    module.exports = app;


`root@u22-128-YT-MACHINE:~/mean# pm2 start server.js`

`root@u22-128-YT-MACHINE:~/mean# pm2 startup`

`root@u22-128-YT-MACHINE:~/mean# ss -antpl | grep 3000`

    http://localhost:3000/

<br>


### Configure Nginx as a Reverse Proxy For MEAN,

`root@u22-128-YT-MACHINE:~# cd`

`root@u22-128-YT-MACHINE:~# apt-get install nginx -y`

<br>

`root@u22-128-YT-MACHINE:~# nano /etc/nginx/conf.d/mean.conf`

<br>

    server {
    listen 80;
    
    server_name 192.168.56.128;
    access_log /var/log/nginx/mean-access.log;
    error_log /var/log/nginx/mean-error.log;
    
    location / {
    proxy_set_header X-Forwarded-Host $host;
    proxy_set_header X-Forwarded-Server $host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_pass http://localhost:3000/;
    }
    }


`root@u22-128-YT-MACHINE:~# nano /etc/nginx/nginx.conf`

    # server_names_hash_bucket_size 64;

`root@u22-128-YT-MACHINE:~# nginx -t`

<br>

`root@u22-128-YT-MACHINE:~# systemctl restart nginx`

`root@u22-128-YT-MACHINE:~# systemctl enable nginx`

`root@u22-128-YT-MACHINE:~# systemctl status nginx`


### Access MEAN Application,

    http://192.168.56.128/
