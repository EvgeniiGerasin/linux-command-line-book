# Обновление информации о пакетах - apt update

Команда **`apt update`** используется в дистрибутивах на основе Debian обновляет информацию о доступных пакетах из репозиториев. Она скачивает данные о пакетах из репозиториев, которые указаны в файлах `/etc/apt/sources.list` и `/etc/apt/sources.list.d/`.

```
gerasin@DESKTOP-9IF30U0:~$ ls -l /etc/apt/
total 28
drwxr-xr-x 2 root root 4096 Nov 30 13:40 apt.conf.d
drwxr-xr-x 2 root root 4096 May 25  2023 auth.conf.d
drwxr-xr-x 2 root root 4096 May 25  2023 keyrings
drwxr-xr-x 2 root root 4096 May 25  2023 preferences.d
-rw-r--r-- 1 root root  229 Nov 30 13:41 sources.list
drwxr-xr-x 2 root root 4096 Dec 22 13:00 sources.list.d
drwxr-xr-x 2 root root 4096 Nov 30 13:40 trusted.gpg.d
```

Важно понимать, что команда только обновляет локальную информации о пакетах, но не устанавливает или не обновляет их.

Обновлять информацию нужно чтобы система знала о последних версиях пакетов и их доступности перед установкой или обновлением. По этому перед установкой пакетов рекомендуется использовать `apt update`.

```
gerasin@DESKTOP-9IF30U0:~$ sudo apt update
[sudo] password for gerasin:
Hit:1 http://deb.debian.org/debian bookworm InRelease
Get:2 http://deb.debian.org/debian bookworm-updates InRelease [55.4 kB]
Get:3 http://ftp.debian.org/debian bookworm-backports InRelease [59.0 kB]
.
.
.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

Для получения списка пакет, которые могут быть обновлены используется аргумент `list` c опцией `--upgradable`.

```
gerasin@DESKTOP-9IF30U0:~$ apt list --upgradable
Listing... Done
docker-buildx-plugin/bookworm 0.21.1-1~debian.12~bookworm amd64 [upgradable from: 0.20.0-1~debian.12~bookworm]
docker-ce-cli/bookworm 5:28.0.1-1~debian.12~bookworm amd64 [upgradable from: 5:27.5.1-1~debian.12~bookworm]
docker-ce-rootless-extras/bookworm 5:28.0.1-1~debian.12~bookworm amd64 [upgradable from: 5:27.5.1-1~debian.12~bookworm]
docker-ce/bookworm 5:28.0.1-1~debian.12~bookworm amd64 [upgradable from: 5:27.5.1-1~debian.12~bookworm]
docker-compose-plugin/bookworm 2.33.1-1~debian.12~bookworm amd64 [upgradable from: 2.32.4-1~debian.12~bookworm]
libgnutls30/stable-security 3.7.9-2+deb12u4 amd64 [upgradable from: 3.7.9-2+deb12u3]
openssh-client/stable-security 1:9.2p1-2+deb12u5 amd64 [upgradable from: 1:9.2p1-2+deb12u4]
```
