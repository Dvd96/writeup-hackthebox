Cosa fare:

1) lanciare nmap, ci sono servizi a porta 80
2) andare su porta 80 e c'è sito web con instruzioni
3) lanciare gobuster, dirb ecc. Usando dirbuster si trova quasi subito un importante path:
4) /scanner.php
5) qui praticamente possiamo lanciare nmap, ci sono dei controlli su caratteri come ; & | che non potranno essere utilizzati per rce
6) usiamo quindi burp, grazie a lui potremo lanciare comandi semplicemente scrivendoli sotto host=
7) da qui basta stamparsi le varie flag
8) prima flag : cat s1kr3t/flag.txt
9) seconda flag: /root/code/reader /home/craven/flag.txt
10) terza flag: /root/code/reader /home/craven/flag.txt /home/vulnhub/flag.txt