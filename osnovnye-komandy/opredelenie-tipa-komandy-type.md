# Определение типа команды - type

Команда `type` помогает понять, как именно оболочка обрабатывает указанную команду. Это особенно полезно, когда у вас есть несколько команд с одинаковыми именами (например, алиас и внешняя программа), и вы хотите узнать, какая из них будет выполнена по умолчанию.

```
gerasin@DESKTOP-9IF30U0:~$ type ls
ls is aliased to `ls --color=auto'

gerasin@DESKTOP-9IF30U0:~$ type cp
cp is hashed (/usr/bin/cp)

gerasin@DESKTOP-9IF30U0:~$ type mkdir
mkdir is hashed (/usr/bin/mkdir)

gerasin@DESKTOP-9IF30U0:~$ type type
type is a shell builtin
```
