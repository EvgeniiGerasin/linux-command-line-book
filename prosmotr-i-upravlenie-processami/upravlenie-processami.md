# Управление процессами

Для примера управления процессом будет использоваться программа ping, которая проверяет связь с указанным сервером (сайтом) и измеряет время отклика.

```
gerasin@DESKTOP-9IF30U0:~$ sudo ping yandex.ru
[sudo] password for gerasin:
PING yandex.ru (5.255.255.77) 56(84) bytes of data.
64 bytes from yandex.ru (5.255.255.77): icmp_seq=1 ttl=46 time=103 ms
64 bytes from yandex.ru (5.255.255.77): icmp_seq=2 ttl=46 time=107 ms
64 bytes from yandex.ru (5.255.255.77): icmp_seq=3 ttl=46 time=103 ms
64 bytes from yandex.ru (5.255.255.77): icmp_seq=4 ttl=46 time=103 ms
64 bytes from yandex.ru (5.255.255.77): icmp_seq=5 ttl=46 time=103 ms
```

## Прерывание процесса

Вывод программы `ping` бесконечный. Для остановки вывода можно использовать сочетание клавиш `CTRL+C`.

```
gerasin@DESKTOP-9IF30U0:~$ sudo ping yandex.ru
[sudo] password for gerasin:
PING yandex.ru (5.255.255.77) 56(84) bytes of data.
64 bytes from yandex.ru (5.255.255.77): icmp_seq=1 ttl=46 time=103 ms
64 bytes from yandex.ru (5.255.255.77): icmp_seq=2 ttl=46 time=103 ms
^C
--- yandex.ru ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 102.895/103.083/103.272/0.188 ms
```

Данная комбинация прерывает выполнение программы и плавно ее завершает. Так можно завершать выполнение почти всех программ.

{% hint style="info" %}
В Unix-подобных системах символ `^` означает клавишу `ctrl`. Запись в терминале `^C` эквивалента `CTRL+C`.
{% endhint %}

## Перевод выполнения в фоновый режим

Во время работы программы `ping` нельзя использовать командную оболочку. Для устранения этого можно перевести выполнение в фоновый режим. Для этого используется параметр `&`.

```
gerasin@DESKTOP-9IF30U0:~$ sudo ping yandex.ru &> /dev/null &
[3] 949
```

Для удобства перенаправляем вывод `ping` в файл `/dev/null`. После выполнения команды на экране появится информация от механизма управления задачам. `[3]` — номер запущенного задания, `949` — PID процесса.

Для просмотра запущенного процесса используется команда `ps -p 949`

```
gerasin@DESKTOP-9IF30U0:~$ ps -p 949
    PID TTY          TIME CMD
    949 pts/0    00:00:00 sudo
```

Механизм управления задачами может вывести список запущенных задач. Для этого используется команда `jobs`.

```
gerasin@DESKTOP-9IF30U0:~$ jobs
[3]-  Running                 sudo ping yandex.ru &> /dev/null &
```

## Выход из фонового режима

Для того чтобы вытащить программу из фонового режима используется команда `fg %<номер запущенного задания>`.

```
gerasin@DESKTOP-9IF30U0:~$ fg %3
sudo ping yandex.ru &> /dev/null
```

Для завершения процесса используется команда `CTRL+C`.

## Приостановка процесса

Для остановки выполнения процесса (программы) на время используется комбинация клавиш `CTRL+Z`.

```
gerasin@DESKTOP-9IF30U0:~$ sudo ping yandex.ru &> /dev/null
^Z
[3]+  Stopped                 sudo ping yandex.ru &> /dev/null
```

```
gerasin@DESKTOP-9IF30U0:~$ jobs
[3]+  Stopped                 sudo ping yandex.ru &> /dev/null
```

Теперь можно перезапустить остановленный процесс или перевести ее в фоновый режим командой `bg`, аналогичной `fg`.

```
gerasin@DESKTOP-9IF30U0:~$ bg $3
[3]+ sudo ping yandex.ru &> /dev/null &
```

```
gerasin@DESKTOP-9IF30U0:~$ jobs
[3]-  Running                 sudo ping yandex.ru &> /dev/null &
```

## Отправка сигналов процессам

При нажатии `CTRL+C` или `CTRL+Z` происходит отправка сигналов на завершение и приостановку процесса. Кроме них еще и другие. Для просмотра доступных процессов используется команда `kill` с параметров `-l`.

```
gerasin@DESKTOP-9IF30U0:~$ kill -l
 1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP
 2) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1
1) SIGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM
2) SIGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
3) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ
4) SIGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR
5) SIGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
6) SIGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
7) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
8) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
9) SIGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
10) SIGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
11) SIGRTMAX-1  64) SIGRTMAX
```

При сочетании `CTRL+C` посылается сигнал `INT`, а при `CTRL+Z` — `TSTP`.

Для ручного управления сигналами используется команда `kill -<сигнал> <PID>`.

```
gerasin@DESKTOP-9IF30U0:~$ jobs -l
[3]-  1074 Running                 sudo ping yandex.ru &> /dev/null &
```

```
gerasin@DESKTOP-9IF30U0:~$ kill -SIGTSTP 1074
gerasin@DESKTOP-9IF30U0:~$ jobs
[3]+  Stopped                 sudo ping yandex.ru &> /dev/null
```

Для возобновления работы пошлем сигнал `SIGCONT`.

```
gerasin@DESKTOP-9IF30U0:~$ kill -SIGCONT 1074
gerasin@DESKTOP-9IF30U0:~$ jobs
[3]-  Running                 sudo ping yandex.ru &> /dev/null &
```

> \[!note] Вместо `-SIGCONT` можно ввести норм сигнала `18`: `kill -18 1074`

#### Часто используемые сигналы

| Номер | Имя  | Значение                                                                                                           |
| ----- | ---- | ------------------------------------------------------------------------------------------------------------------ |
| 1     | HUP  | Обрыв связи. Используется для завершения программ при потере терминала или перезапуска демонов (например, Apache). |
| 2     | INT  | Прервать. Аналог нажатия CTRL+C. Обычно завершает программу.                                                       |
| 9     | KILL | Уничтожить. Немедленно завершает процесс без возможности обработки.                                                |
| 15    | TERM | Завершить. Сигнал по умолчанию для команды `kill`. Программа завершается, если может обработать сигнал.            |
| 18    | CONT | Продолжить. Восстанавливает работу процесса после сигнала STOP.                                                    |
| 19    | STOP | Приостановить. Останавливает процесс без завершения. Не может быть проигнорирован.                                 |
| 20    | TSTP | Сигнал «стоп» с клавиатуры. Аналог нажатия CTRL+Z. Может быть проигнорирован программой.                           |
