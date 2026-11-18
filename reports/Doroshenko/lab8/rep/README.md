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

### 1.1 Базовое сканирование портов

1) Выполним базовое сканирование

Команда: `nmap scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-18 21:37 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.20s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 995 closed tcp ports (conn-refused)
PORT     STATE    SERVICE
9/tcp    filtered discard
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
9929/tcp open     nping-echo

Nmap done: 1 IP address (1 host up) scanned in 16.36 seconds
```

2) Выполним SYN-сканирование

Команда: `sudo nmap -sS scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-18 21:38 +03
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

Nmap done: 1 IP address (1 host up) scanned in 11.65 seconds
```

3) Выполним TCP connect-сканирование

Команда: `nmap -sT scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-18 21:38 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.20s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 995 closed tcp ports (conn-refused)
PORT     STATE    SERVICE
9/tcp    filtered discard
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
9929/tcp open     nping-echo

Nmap done: 1 IP address (1 host up) scanned in 13.07 seconds
```

Полученные результаты приведу в таблице для сравнения

| Метод сканирования | Порт | Состояние | Сервис |
| --- | --- | --- | --- |
| Базовое сканирование | `9/tcp` | `filtered` | `discard` |
| | `22/tcp ` | `open` | `ssh` |
| | `25/tcp` | `filtered` | `smtp` |
| | `80/tcp` | `open` | `http` |
| | `9929/tcp` | `open` | `nping-echo` |
| SYN-сканирование | `9/tcp` | `filtered` | `discard` |
| | `22/tcp ` | `open` | `ssh` |
| | `25/tcp` | `filtered` | `smtp` |
| | `80/tcp` | `open` | `http` |
| | `9929/tcp` | `open` | `nping-echo` |
|  TCP connect-сканирование | `9/tcp` | `filtered` | `discard` |
| | `22/tcp ` | `open` | `ssh` |
| | `25/tcp` | `filtered` | `smtp` |
| | `80/tcp` | `open` | `http` |
| | `9929/tcp` | `open` | `nping-echo` |

### 1.2 Сканирование диапазона портов и конкретных портов

1) Просканируем популярные порты

Команда: `nmap -p 1-1000 scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-18 21:56 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.20s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 996 closed tcp ports (conn-refused)
PORT   STATE    SERVICE
9/tcp  filtered discard
22/tcp open     ssh
25/tcp filtered smtp
80/tcp open     http

Nmap done: 1 IP address (1 host up) scanned in 13.93 seconds
```

2) Просканируем конкретные порты

Команда: `nmap -p 22,80,443 scanme.nmap.org`

Результат:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-11-18 21:59 +03
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.25s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f

PORT    STATE  SERVICE
22/tcp  open   ssh
80/tcp  open   http
443/tcp closed https

Nmap done: 1 IP address (1 host up) scanned in 0.55 seconds
```

### 1.3 Определение версий служб

1) Запустим сканирование с определением версий

Команда: `nmap -sV scanme.nmap.org`

Результат:
```

```

2) Усилим определение версий 

Команда: `nmap -sV --version-idensity 9 scanme.nmap.org`

Результат:
```

```

## Задание 2

Определите операционную систему этой же машины.



## Задание 3

Узнайте адреса активных хостов в сети лаборатории (без сканирования портов).

## Задание 4

Просканируйте хост №1, разными методами. Сравните результаты.

## Задание 5

Для четырех хостов (№2-5), выполните следующие действия:

### 5.1 Определите, защищен ли хост межсетевым экраном

### 5.2 Определите поддерживаемые протоколы.

### 5.3 Выберите оптимальный метод сканирования портов, чтобы избежать обнаружения. Определите открытые и фильтрованные порты и по возможности версии служб. При необходимости используйте RPC-сканирование.

### 5.4 Определите операционную систему.


---

# Выводы

В ходе выполнения лабораторной работы я примененил утилиты для сканирования и исследования безопасности сети nmap.
