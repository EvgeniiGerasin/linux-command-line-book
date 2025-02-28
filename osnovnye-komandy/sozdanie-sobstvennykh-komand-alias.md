# Создание собственных команд - alias

Команда `alias` используется для создания псевдонимов (коротких имен) для команд или их комбинаций. Это позволяет упростить выполнение часто используемых команд или сократить длинные команды до более удобных форм.

Например команда ls это алиас. Под капотом этой команды находится `ls --color=auto`.

```
gerasin@DESKTOP-9IF30U0:~$ type ls
ls is aliased to `ls --color=auto'
```

Синтаксис команды: `alias имя_алиаса= 'команда'`

Например создадим алиас для команды `ls -lt`, которая выводит информацию о файла и каталогах в порядке убывания даты создания. Перед созданием лучше проверить свободно ли имя.

```
gerasin@DESKTOP-9IF30U0:~$ type lsl
-bash: type: lsl: not found
```

```
gerasin@DESKTOP-9IF30U0:~$ alias lsl='ls -lt'

gerasin@DESKTOP-9IF30U0:~$ lsl
total 12
drwxr-xr-x 5 gerasin gerasin 4096 Feb 21 12:32 documents
-rw-r--r-- 1 gerasin gerasin    0 Feb 21 12:32 file.txt
drwxr-xr-x 2 gerasin gerasin 4096 Feb 21 10:56 work
drwxrwxrwx 3 gerasin gerasin 4096 Feb 13 11:34 project

gerasin@DESKTOP-9IF30U0:~$ type lsl
lsl is aliased to `ls -lt'
```

Для просмотра всех алиасов достаточно ввести команду `alias` без аргументов.

```
gerasin@DESKTOP-9IF30U0:~$ alias
alias ls='ls --color=auto'
alias lsl='ls -lt'
```

Алиасы сохраняются только для текущего сеанса. Чтобы они сохранялись после перезапуска терминала, их нужно добавить в конфигурационный файл оболочки.

В зависимости от оболочки, файлы конфигурации могут отличаться:

* **Bash** : `.bashrc` или `.bash_profile`
* **Zsh** : `.zshrc`
* **Fish** : \`config.fish'

```
gerasin@DESKTOP-9IF30U0:~$ ls -la
-rw-r--r--  1 gerasin gerasin  3616 Feb 17 09:50 .bashrc
```

В файл `.bashrc` необходимо добавить строку `alias lsl='ls -lt`, сохранить изменения и перезагрузить сессию оболочки. Открыть и отредактировать его можно например программой `nano`.
