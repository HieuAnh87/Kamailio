# INSTALL KAMAILIO ON UBUNTU 20.04

#### B1: Install MariaDB DB Server

```
sudo apt update 
sudo apt install mariadb-server
```
#### B2: Add Kamailio apt repository

```
wget -O- http://deb.kamailio.org/kamailiodebkey.gpg | sudo apt-key add -
```
Then add the repository lines to /etc/apt/sources.list

```
sudo tee /etc/apt/sources.list.d/kamailio.list<<EOF
deb     http://deb.kamailio.org/kamailio57 focal main
deb-src http://deb.kamailio.org/kamailio57 focal main
EOF
```

#### B3: Install Kamailio 

```
sudo apt update
sudo apt install kamailio kamailio-mysql-modules
sudo apt install kamailio-websocket-modules kamailio-tls-modules
```

Check kamailio available:

```
$ which kamailio
/usr/sbin/kamailio

$ kamailio -V
version: kamailio 5.7.0 (x86_64/linux) 
flags: USE_TCP, USE_TLS, USE_SCTP, TLS_HOOKS, USE_RAW_SOCKS, DISABLE_NAGLE, USE_MCAST, DNS_IP_HACK, SHM_MMAP, PKG_MALLOC, MEM_JOIN_FREE, Q_MALLOC, F_MALLOC, TLSF_MALLOC, DBG_SR_MEMORY, USE_FUTEX, FAST_LOCK-ADAPTIVE_WAIT, USE_DNS_CACHE, USE_DNS_FAILOVER, USE_NAPTR, USE_DST_BLOCKLIST, HAVE_RESOLV_RES, TLS_PTHREAD_MUTEX_SHARED
ADAPTIVE_WAIT_LOOPS 1024, MAX_RECV_BUFFER_SIZE 262144, MAX_URI_SIZE 1024, BUF_SIZE 65535, DEFAULT PKG_SIZE 8MB
poll method support: poll, epoll_lt, epoll_et, sigio_rt, select.
id: unknown 
compiled with gcc 9.4.0
```



#### B4: Configure Kamailio
- config kamctlrc (config như file [kamctltrc](https://github.com/HieuAnh87/kamailio/-/blob/main/kamctlrc)))
```
sudo vim /etc/kamailio/kamctlrc
$ sudo kamdbctl create
```

- MYSQL:
root: Vcc123** / kamailio: kamailiorw

- Setup SIP domain

```
$ sudo vim /etc/kamailio/kamctlrc
## SIP domain
SIP_DOMAIN= 1xx.xxx.xxx
```
- Add these lines below #!KAMAILIO.

```
$ sudo vim /etc/kamailio/kamailio.cfg
#!define WITH_MYSQL
#!define WITH_AUTH
#!define WITH_USRLOCDB
#!define WITH_ACCDB
```
- Restart Kamailio service:

```
sudo systemctl restart kamailio
sudo systemctl status kamailio
```
