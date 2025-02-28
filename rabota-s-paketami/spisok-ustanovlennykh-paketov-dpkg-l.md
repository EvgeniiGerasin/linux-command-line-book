# Список установленных пакетов - dpkg -l

Для получения списка установленных пакетов используется команда `dpkg` с опцией `-l`.

```
gerasin@DESKTOP-9IF30U0:~$ dpkg -l
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                        Architecture Description
+++-===============================-==============================-============-=======================================>
ii  adduser                         3.134                          all          add and remove users and groups
ii  adwaita-icon-theme              43-1                           all          
.
.
.
```

Для проверки установлен пакет или нет используется параметр `-s <имя пакета>` .

```
gerasin@DESKTOP-9IF30U0:~$ dpkg -s htop
dpkg-query: package 'htop' is not installed and no information is available
```

```
gerasin@DESKTOP-9IF30U0:~$ dpkg -s python3.11
Package: python3.11
Status: install ok installed
Priority: optional
.
.
.
```
