# CONFIG LOG KAMAILIO

#### B1: Config logrotate
 - Open file for rsyslog at /etc/rsyslog.conf:

```
$ sudo vim /etc/rsyslog.conf
```

- Add rule for message sended from Kamailio, in my case identified by local0, which will be saved into a special file for kamailio logging, here /var/log/kamailio.log
```
###############
#### RULES ####
###############

local0.*                        -/var/log/kamailio.log
```
- Restart rsyslog service:
```
/etc/init.d/rsyslog restart
Stopping enhanced syslogd: rsyslogd.
Starting enhanced syslogd: rsyslogd.
```
- Add vào kamailio.cfg:
```
$ sudo vim /etc/kamailio/kamailio.cfg
log_facility=LOG_LOCAL0
sudo service kamailio restart
```

## In kamailio
Kamailio cho phép config nhiều level log khác nhau, [tại đây](http://www.kamailio.org/dokuwiki/doku.php/tutorials:debug-syslog-messages).

Nói chung, Logging trong Kamailio có thể config sử dụng các option sau:
+ debug – set log level, this is number between 0 and 9. Default is 0. The higher the number the more information will be written to the log. The default level (if no debug is present in the config file and no -d parameter on the command line) is 2 (L_NOTICE).
+ log_stderror – if set to “yes”, the server will print its debugging information to standard error output. If set to “no”, syslog will be used. Default is “no” (printing to syslog).
+ memlog – debugging level for final memory statistics report. Default is “L_DBG” – memory statistics are dumped only if “debug” option has higher value.
+ log_facility – is used to specify what type of program is logging the message. Valid values to use with OpenSER are “LOG_LOCAL0” through “LOG_LOCAL7”. See the manual page of syslog for more information.

#### Setting up debug level
- Open file kamailio.cfg and add these lines below "####### Global Parameters #########":
```
debug=3    # 
memdbg=4   # memory debugging is not active as the debug level is lower than memdbg
memlog=4   # dumping of memory statistics is not active as the debug level is lower than memlog
```
### Use
##### Cách 1
```
tail -f /var/log/kamailio.log
```
##### Cách 2: Run in frontend:
```
kamailio -dd -D 2
```
###### or
```
kamailio -M 8 -E -e -dd
```

