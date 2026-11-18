<p align="center">Министерство образования Республики Беларусь</p>
<p align="center">Учреждение образования</p>
<p align="center">“Брестский Государственный технический университет”</p>
<p align="center">Кафедра ИИТ</p>
<br><br><br><br><br><br><br>
<p align="center">Лабораторная работа №8</p>
<p align="center">По дисциплине “Аппаратное и Программное обеспечение сетей”</p>
<p align="center">Тема: “Утилита для сканирования и исследования безопасности сети NMAP”</p>
<p align="center">Вариант: 7</p>
<br><br><br><br><br>
<p align="right">Выполнил:</p>
<p align="right">Студент 3 курса</p>
<p align="right">Группы ИИ-27</p>
<p align="right">Дорошенко М.Д.</p>
<p align="right">Проверил:</p>
<p align="right">Кулик А.Д.</p>
<br><br><br><br><br>
<p align="center">Брест 2026</p>

---

# Цель

Изучение и практическое применение утилиты для сканирования и
исследования безопасности сети nmap.

# Ход работы

## Задание 1

Получите список открытых портов (TCP и UDP) машины, за которой выполняется
лабораторная работа (localhost). Воспользуйтесь несколькими методами
сканирования. Сравните результаты.

1) Выполним TCP-SYN сканирование

Команда: `sudo nmap -sS 127.0.0.1`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 01:34 +03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000020s latency).
Not shown: 997 closed tcp ports (reset)
PORT     STATE SERVICE
80/tcp   open  http
631/tcp  open  ipp
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 0.05 seconds
```

2) Выполним TCP connect сканирование

Команда: `sudo nmap -sT 127.0.0.1`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 01:35 +03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000064s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT     STATE SERVICE
80/tcp   open  http
631/tcp  open  ipp
8443/tcp open  https-alt

Nmap done: 1 IP address (1 host up) scanned in 0.03 seconds
```

3) Выполним UDP-сканирование

Команда: `sudo nmap -sU --top-ports 50 127.0.0.1`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 01:37 +03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000050s latency).
Not shown: 49 closed udp ports (port-unreach)
PORT     STATE         SERVICE
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.29 seconds
```

## Задание 2

Определите операционную систему этой же машины.

Команда: `sudo nmap -O 127.0.0.1`

```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 01:38 +03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000072s latency).
Not shown: 997 closed tcp ports (reset)
PORT     STATE SERVICE
80/tcp   open  http
631/tcp  open  ipp
8443/tcp open  https-alt
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=11/19%OT=80%CT=1%CU=41532%PV=N%DS=0%DC=L%G=Y%TM=6AF
OS:E28F9%P=x86_64-pc-linux-gnu)SEQ(SP=101%GCD=1%ISR=10F%TI=Z%CI=Z%II=I%TS=2
OS:2)OPS(O1=MFFD7ST11NWA%O2=MFFD7ST11NWA%O3=MFFD7NNT11NWA%O4=MFFD7ST11NWA%O
OS:5=MFFD7ST11NWA%O6=MFFD7ST11)WIN(W1=FFCB%W2=FFCB%W3=FFCB%W4=FFCB%W5=FFCB%
OS:W6=FFCB)ECN(R=Y%DF=Y%T=40%W=FFD7%O=MFFD7NNSNWA%CC=Y%Q=)T1(R=Y%DF=Y%T=40%
OS:S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%
OS:RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W
OS:=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)
OS:U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%D
OS:FI=N%T=40%CD=S)

Network Distance: 0 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.28 seconds
```


## Задание 3

Узнайте адреса активных хостов в сети лаборатории (без сканирования портов).

Команда: `sudo nmap -sn scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:02 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.24s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Nmap done: 1 IP address (1 host up) scanned in 0.36 seconds

```

## Задание 4

Просканируйте хост №1, разными методами. Сравните результаты.

1) Сканирование SYN методом

Команда: `sudo nmap -sS scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:02 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.20s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 995 closed tcp ports (reset)
PORT     STATE    SERVICE
9/tcp    filtered discard
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
9929/tcp open     nping-echo

Nmap done: 1 IP address (1 host up) scanned in 10.90 seconds
```

2) Сканирование TCP connect методом

Команда: `sudo nmap -sT scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:03 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.21s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 995 closed tcp ports (conn-refused)
PORT     STATE    SERVICE
9/tcp    filtered discard
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
9929/tcp open     nping-echo

Nmap done: 1 IP address (1 host up) scanned in 15.96 seconds
```

3) Сканирование FIN методом

Команда: `sudo nmap -sF scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:03 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.30s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
All 1000 scanned ports on scanme.nmap.org (45.33.32.156) are in ignored states.
Not shown: 1000 open|filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 301.64 seconds
```

4) Сканирование Xmas методом

Команда: `sudo nmap -sX scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:06 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.24s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
All 1000 scanned ports on scanme.nmap.org (45.33.32.156) are in ignored states.
Not shown: 1000 open|filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 25.60 seconds
```

5) Сканирование NULL методом

Команда: `sudo nmap -sN scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:06 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.22s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
All 1000 scanned ports on scanme.nmap.org (45.33.32.156) are in ignored states.
Not shown: 1000 open|filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 226.56 seconds
```

## Задание 5

Перед этим заданием определим хосты №2-5:
* scanme.nmap.org
* localhost
* 192.168.100.30/24
* 172.17.0.1/16

Для четырех хостов (№2-5), выполните следующие действия:

### 5.1 Определите, защищен ли хост межсетевым экраном

Команда: `sudo nmap -sA <IP_хоста>`

Результат для №2:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:16 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.29s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
All 1000 scanned ports on scanme.nmap.org (45.33.32.156) are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)

Nmap done: 1 IP address (1 host up) scanned in 296.33 seconds
```

Результат для №3:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:20 +03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000020s latency).
All 1000 scanned ports on localhost (127.0.0.1) are in ignored states.
Not shown: 1000 unfiltered tcp ports (reset)

Nmap done: 1 IP address (1 host up) scanned in 0.04 seconds
```

Результат для №4:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:20 +03
Nmap scan report for 192.168.100.1
Host is up (0.015s latency).
Not shown: 996 unfiltered tcp ports (reset)
PORT   STATE    SERVICE
21/tcp filtered ftp
22/tcp filtered ssh
23/tcp filtered telnet
80/tcp filtered http
MAC Address: 60:F1:8A:47:89:9C (Huawei Technologies)

Nmap scan report for 192.168.100.46
Host is up (0.011s latency).
All 1000 scanned ports on 192.168.100.46 are in ignored states.
Not shown: 1000 unfiltered tcp ports (reset)
MAC Address: CA:29:D9:71:05:27 (Unknown)

Nmap scan report for 192.168.100.30
Host is up (0.0000030s latency).
All 1000 scanned ports on 192.168.100.30 are in ignored states.
Not shown: 1000 unfiltered tcp ports (reset)

Nmap done: 256 IP addresses (3 hosts up) scanned in 40.54 seconds
```

Результат для №5:
```

```

### 5.2 Определите поддерживаемые протоколы.

Команда: `sudo nmap -sO <IP_хоста>`

Результат для №2:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:22 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.25s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 254 open|filtered n/a protocols (no-response)
PROTOCOL STATE SERVICE
1        open  icmp
17       open  udp

Nmap done: 1 IP address (1 host up) scanned in 10.55 seconds
```

Результат для №3:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:23 +03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0000080s latency).
Not shown: 249 closed n/a protocols (proto-unreach)
nmap: protocols.cc:193: const nprotoent* nmap_getprotbynum(int): Assertion `num >= 0 && num < UCHAR_MAX' failed.
Аварийный останов
```

Результат для №4:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:24 +03
Warning: 192.168.100.1 giving up on port because retransmission cap hit (10).
Nmap scan report for 192.168.100.1
Host is up (0.012s latency).
Not shown: 247 closed n/a protocols (proto-unreach)
PROTOCOL STATE         SERVICE
1        open          icmp
2        open|filtered igmp
4        open|filtered ipv4
6        open|filtered tcp
17       open          udp
41       open|filtered ipv6
47       open|filtered gre
103      open|filtered pim
136      open|filtered udplite
MAC Address: 60:F1:8A:47:89:9C (Huawei Technologies)

Nmap scan report for 192.168.100.46
Host is up (0.27s latency).
Not shown: 242 closed n/a protocols (proto-unreach)
PROTOCOL STATE         SERVICE
1        open          icmp
2        open|filtered igmp
4        open|filtered ipv4
6        open          tcp
17       open          udp
33       open|filtered dccp
41       open|filtered ipv6
47       open|filtered gre
50       open|filtered esp
51       open|filtered ah
108      open|filtered ipcomp
132      open|filtered sctp
136      open|filtered udplite
253      open|filtered experimental1
MAC Address: CA:29:D9:71:05:27 (Unknown)

Nmap scan report for 192.168.100.30
Host is up (0.0000080s latency).
Not shown: 249 closed n/a protocols (proto-unreach)
nmap: protocols.cc:193: const nprotoent* nmap_getprotbynum(int): Assertion `num >= 0 && num < UCHAR_MAX' failed.
Аварийный останов
```

Результат для №5:
```
----
```

### 5.3 Выберите оптимальный метод сканирования портов, чтобы избежать обнаружения. Определите открытые и фильтрованные порты и по возможности версии служб. При необходимости используйте RPC-сканирование.

Команда: `sudo nmap -sV -p- -T2 <IP_хоста>`

Результат для №2:
```

```

Результат для №3:
```

```

Результат для №4:
```

```

Результат для №5:
```

```

### 5.4 Определите операционную систему.

Команда: `sudo nmap -O <IP_хоста>`

Результат для №2:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:31 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.20s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 995 closed tcp ports (reset)
PORT     STATE    SERVICE
9/tcp    filtered discard
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
9929/tcp open     nping-echo
Aggressive OS guesses: Linux 2.6.32 (89%), Linux 2.6.39 (89%), Linux 3.10 - 3.12 (89%), Linux 3.4 (89%), Linux 3.5 (89%), Linux 4.2 (89%), Linux 4.4 (89%), Synology DiskStation Manager 5.1 (89%), Linux 2.6.35 (88%), Linux 3.10 (88%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 24 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 23.39 seconds
```

Результат для №3:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:32 +03
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000074s latency).
Not shown: 997 closed tcp ports (reset)
PORT     STATE SERVICE
80/tcp   open  http
631/tcp  open  ipp
8443/tcp open  https-alt
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=11/19%OT=80%CT=1%CU=34908%PV=N%DS=0%DC=L%G=Y%TM=6AF
OS:E359C%P=x86_64-pc-linux-gnu)SEQ(SP=106%GCD=1%ISR=108%TI=Z%CI=Z%II=I%TS=2
OS:1)OPS(O1=MFFD7ST11NWA%O2=MFFD7ST11NWA%O3=MFFD7NNT11NWA%O4=MFFD7ST11NWA%O
OS:5=MFFD7ST11NWA%O6=MFFD7ST11)WIN(W1=FFCB%W2=FFCB%W3=FFCB%W4=FFCB%W5=FFCB%
OS:W6=FFCB)ECN(R=Y%DF=Y%T=40%W=FFD7%O=MFFD7NNSNWA%CC=Y%Q=)T1(R=Y%DF=Y%T=40%
OS:S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%
OS:RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W
OS:=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)
OS:U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%D
OS:FI=N%T=40%CD=S)

Network Distance: 0 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.28 seconds
```

Результат для №4:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-19 02:33 +03
Nmap scan report for 192.168.100.1
Host is up (0.0065s latency).
Not shown: 993 closed tcp ports (reset)
PORT      STATE    SERVICE
21/tcp    filtered ftp
22/tcp    filtered ssh
23/tcp    filtered telnet
53/tcp    open     domain
80/tcp    filtered http
3333/tcp  open     dec-notes
49152/tcp open     unknown
MAC Address: 60:F1:8A:47:89:9C (Huawei Technologies)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=11/19%OT=53%CT=1%CU=41090%PV=Y%DS=1%DC=D%G=Y%M=60F1
OS:8A%TM=6AFE3639%P=x86_64-pc-linux-gnu)SEQ(SP=102%GCD=1%ISR=105%TI=Z%CI=I%
OS:II=I%TS=7)SEQ(SP=102%GCD=1%ISR=106%TI=Z%CI=I%II=I%TS=7)OPS(O1=M5B4ST11NW
OS:2%O2=M5B4ST11NW2%O3=M5B4NNT11NW2%O4=M5B4ST11NW2%O5=M5B4ST11NW2%O6=M5B4ST
OS:11)WIN(W1=3890%W2=3890%W3=3890%W4=3890%W5=3890%W6=3890)ECN(R=Y%DF=Y%T=40
OS:%W=3908%O=M5B4NNSNW2%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R
OS:=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W
OS:=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)
OS:T7(R=N)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)I
OS:E(R=Y%DFI=N%T=40%CD=S)

Network Distance: 1 hop

Nmap scan report for 192.168.100.46
Host is up (0.044s latency).
All 1000 scanned ports on 192.168.100.46 are in ignored states.
Not shown: 1000 closed tcp ports (reset)
MAC Address: CA:29:D9:71:05:27 (Unknown)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for 192.168.100.62
Host is up (0.094s latency).
All 1000 scanned ports on 192.168.100.62 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 8E:0C:B5:EF:8D:43 (Unknown)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: switch|VoIP phone
Running: Dell embedded, Grandstream embedded
OS CPE: cpe:/h:dell:powerconnect_2708 cpe:/h:grandstream:gxp2000
OS details: Dell PowerConnect 2708 switch, Grandstream GXP2000 VoIP phone, Grandstream GXP2020 VoIP phone
Network Distance: 1 hop

Nmap scan report for 192.168.100.30
Host is up (0.000083s latency).
Not shown: 998 closed tcp ports (reset)
PORT     STATE SERVICE
80/tcp   open  http
8443/tcp open  https-alt
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=11/19%OT=80%CT=1%CU=39507%PV=Y%DS=0%DC=L%G=Y%TM=6AF
OS:E3644%P=x86_64-pc-linux-gnu)SEQ(SP=103%GCD=1%ISR=10C%TI=Z%CI=Z%TS=20)SEQ
OS:(SP=103%GCD=1%ISR=10C%TI=Z%CI=Z%II=I%TS=20)OPS(O1=MFFD7ST11NWA%O2=MFFD7S
OS:T11NWA%O3=MFFD7NNT11NWA%O4=MFFD7ST11NWA%O5=MFFD7ST11NWA%O6=MFFD7ST11)WIN
OS:(W1=FFCB%W2=FFCB%W3=FFCB%W4=FFCB%W5=FFCB%W6=FFCB)ECN(R=Y%DF=Y%T=40%W=FFD
OS:7%O=MFFD7NNSNWA%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3
OS:(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=
OS:Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=
OS:Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%R
OS:IPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Network Distance: 0 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 256 IP addresses (4 hosts up) scanned in 142.84 seconds
```

Результат для №5:
```
---
```

---

# Выводы

В ходе выполнения лабораторной работы я примененил утилиты для сканирования и исследования безопасности сети nmap.
