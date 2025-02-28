# Создание каталога - mkdir

Команда используется для создания каталогов.

```
gerasin@DESKTOP-9IF30U0:~$ mkdir my-new-dir

gerasin@DESKTOP-9IF30U0:~$ ls -t
my-new-dir
```

Можно создать несколько каталогов одновременно передав список названий каталогов как аргумент.

```
gerasin@DESKTOP-9IF30U0:~$ ls -t
my-new-dir2  my-new-dir3  my-new-dir1
```

Для создания вложенных каталогов необходимо использовать параметр `-p`.

```
gerasin@DESKTOP-9IF30U0:~$ mkdir -p tets-dir/new/my/dir 
gerasin@DESKTOP-9IF30U0:~$ ls -R tets-dir/
tets-dir/:
new

tets-dir/new:
my

tets-dir/new/my:
dir

tets-dir/new/my/dir:
```
