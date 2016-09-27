### tcping.exe

특정 TCP 포트로 Ping 날리는 프로그램 - tcping

C:\Windows\System32 폴더에 복사해두고 일반 윈도우 명령어처럼 수시로 사용

```tex
Usage: tcping [-t] [-d] [-i interval] [-n times] server-address [server-port]

         -t   : ping continuously until stopped via control-c
         -n 5 : for instance, send 5 pings
         -i 5 : for instance, ping every 5 seconds
         -w 100 : for instance, wait 100 milliseconds for a response
         -d   : include date and time on each line
         -b 1 : enable beeps (1 for on-down, 2 for on-up,
                              3 for on-change, 4 for always)
         -r 5 : for instance, relookup the hostname every 5 pings
         -s   : automatically exit on a successful ping
         -v   : print version and exit 

        If you don't pass server-port, it defaults to 80.
```

[블로그 참고 http://snoopybox.co.kr/1576](http://snoopybox.co.kr/1576)

#### 사용방법

예)
```bash
tcping -i 30 -d -t rm-2zeg58sfqi45eq8fc.sqlserver.rds.aliyuncs.com 3433 > 20160927_tcping.log
```