### Обращение к rpi по сети через hostname и dhcp

[https://www.raspberrypi.org/forums/viewtopic.php?p=84170\#p84170](https://www.raspberrypi.org/forums/viewtopic.php?p=84170#p84170)

Огромный плюс метода - клиенты сети получают динамические ip, но к ним есть возможность обращаться через hostname без дополнительных настроек роутера.

Для этого нужно установить samba

```
sudo apt-get install -y samba
```

Всё, теперь к клиентам можно обращаться через hostname, даже через Windows.

Статья по настройке hostname лежит [здесь](https://goldarte.gitbooks.io/dev_notes/content/nastroika-hostname-na-svyazke-rpi+cleverros.html).

