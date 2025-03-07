# Копирование - cp

Команда `cp` используется для копирования файлов и каталогов. Она позволяет создавать точные дубликаты файлов или целых структур каталогов, сохраняя их содержимое.

Структура команды: `cp [что_копировать] [куда_копировать]`

```
gerasin@DESKTOP-9IF30U0:~$ cp file.txt documents/
```

{% hint style="warning" %}


* При копировании каталогов обязательно используйте параметр `-r` или `-R`, иначе команда завершится с ошибкой.
* Если целевой файл уже существует, он будет перезаписан без предупреждения, если не использовать параметр `-i`.
* Параметр `-p` особенно полезен при резервном копировании, так как сохраняет метаданные файла (время изменения, права доступа и т.д.).
{% endhint %}

### Параметров команды

| Параметр    | Описание                                                                         |
| ----------- | -------------------------------------------------------------------------------- |
| `-i`        | Запрашивает подтверждение перед перезаписью существующего файла.                 |
| `-f`        | Форсирует операцию без запроса подтверждения.                                    |
| `-r`или`-R` | Рекурсивно копирует каталоги и их содержимое.                                    |
| `-p`        | Сохраняет атрибуты исходного файла (время создания, права доступа и т.д.).       |
| `-u`        | Копирует файл только если исходный новее или не существует в целевой директории. |
| `-v`        | Выводит подробную информацию о выполняемых действиях.                            |
| `-l`        | Создает жесткие ссылки вместо копирования файлов.                                |
| `-s`        | Создает символические ссылки вместо копирования файлов.                          |
