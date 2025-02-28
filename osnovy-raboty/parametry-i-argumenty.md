# Параметры и аргументы

Команды в Linux обычно используются вместе с дополнительными элементами, которые можно разделить на две группы:

1. **Параметры (опции / флаги)** — они изменяют то, как команда выполняет свою работу.
2. **Аргументы** — это объекты, на которые команду нужно применить, например, файлы или каталоги.

Общая структура команд:

```
команда [параметры] [аргументы]
```

Где:

* `команда` - это само действие, которое мы хотим выполнить.
* `[параметры]` (необязательные) — служат для настройки работы команды, добавляя ей дополнительный функционал или меняя её поведение.
* `[аргументы]` (необязательные) — указывают, к каким конкретно файлам, папкам или другим объектам нужно применить эту команду.
*

```bash
gerasin@DESKTOP-9IF30U0:~$ ls -l /etc
```

* `ls` — это сама команда (список содержимого директории).
* `-l` — это параметр (показывает подробную информацию о файлах).
* `/etc`— это аргумент (директория, которую мы хотим просмотреть).

> \[!note] Параметры команд чувствительны к регистру.

## Информация о команде

Один из удобных способов быстро получить информацию о конкретной команде — это использование параметра `--help`. Этот параметр доступен для большинства команд и предоставляет краткое описание команды, её синтаксиса и возможных опций. Это полезно, когда вам нужно быстро вспомнить основные параметры команды или её назначение, не углубляясь в обширное руководство.

Использование параметра `--help` очень простое. Просто добавьте его после интересующей вас команды. Например, если вы хотите узнать больше о команде `cd`, выполните следующую команду:

```
gerasin@DESKTOP-9IF30U0:~$ cd --help
cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.

    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable. If DIR is "-", it is converted to $OLDPWD.

    The variable CDPATH defines the search path for the directory containing
    DIR.  Alternative directory names in CDPATH are separated by a colon (:).
    A null directory name is the same as the current directory.  If DIR begins
    with a slash (/), then CDPATH is not used.

    If the directory is not found, and the shell option `cdable_vars' is set,
    the word is assumed to be  a variable name.  If that variable has a value,
    its value is used for DIR.

    Options:
      -L        force symbolic links to be followed: resolve symbolic
                links in DIR after processing instances of `..'
      -P        use the physical directory structure without following
                symbolic links: resolve symbolic links in DIR before
                processing instances of `..'
      -e        if the -P option is supplied, and the current working
                directory cannot be determined successfully, exit with
                a non-zero status
      -@        on systems that support it, present a file with extended
                attributes as a directory containing the file attributes

    The default is to follow symbolic links, as if `-L' were specified.
    `..' is processed by removing the immediately previous pathname component
    back to a slash or the beginning of DIR.

    Exit Status:
    Returns 0 if the directory is changed, and if $PWD is set successfully when
    -P is used; non-zero otherwise.
```

В строке `cd [-L|[-P [-e]] [-@]] [dir]` использование скобок определяет, какие параметры могут сочетаться между собой.

Вертикальная черта `|` указывает на **исключающее "или"** . Это значит, что можно выбрать только один из вариантов, разделенных этой чертой. `[-L | [-P [-e]]]` — здесь можно использовать либо `-L`, либо `-P` (возможно с `-e`). Но нельзя одновременно использовать `-L` и `-P`.

Вложенные скобки показывают, какие параметры могут использоваться вместе. Они также определяют приоритет и группировку. `[-P [-e]]` — это означает, что `-e` может использоваться только вместе с `-P`. Без `-P` параметр `-e` недоступен.

`-@` является независимым параметром и может использоваться отдельно от `-L` и `-P` или вместе с одним из них.

`[dir]` — означает, что аргумент `dir` (путь к директории) необязателен.

Необходимо обращать внимание на эти правила.
