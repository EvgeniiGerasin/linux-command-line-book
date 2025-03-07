# Поиск и удаление повторов - uniq

Команда `uniq` используется для обработки текстовых файлов путем удаления повторяющихся строк. Она работает только с соседними строками, то есть строки должны следовать одна за другой, чтобы быть идентифицированными как повторяющиеся. Для этого удобно использовать совместно с командой `sort`.

```
gerasin@DESKTOP-9IF30U0:~$ ls /bin /etc | sort | uniq
```

Если нужно вывести только повторяющиеся строки необходимо использовать параметр `-d`.

```
gerasin@DESKTOP-9IF30U0:~$ ls /bin /etc | sort |uniq -d
```

## Параметры команды

| Параметр | Описание                                          |
| -------- | ------------------------------------------------- |
| -c       | Подсчитывает количество появлений каждой строки   |
| -d       | Показывает только повторяющиеся строки            |
| -i       | Игнорирует регистр при сравнении строк            |
| -u       | Показывает только уникальные строки               |
| -f N     | Игнорирует первые N полей при сравнении строк     |
| -s N     | Игнорирует первые N символов в каждой строке      |
| -w N     | Сравнивает только первые N символов каждой строки |
