
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

