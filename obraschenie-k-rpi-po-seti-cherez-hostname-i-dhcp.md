### Обращение к rpi по сети через hostname и dhcp

[https://www.raspberrypi.org/forums/viewtopic.php?p=84170\#p84170](https://www.raspberrypi.org/forums/viewtopic.php?p=84170#p84170)

Огромный плюс метода - клиенты сети получают динамические ip, но к ним есть возможность обращаться через hostname без дополнительных настроек роутера.

Вначале нужно установить samba и winbind

```
sudo apt-get install samba 
sudo apt-get install winbind
```

В /etc/samba/smb.conf изменить workgroup, чтобы совпадала с домашней группой сети \(как в windows\):

```
workgroup = WORKGROUP
```

По-умолчанию всё так и есть, поэтому в этот файл можно не лезть.

В /etc/nsswitch.conf нужно изменить настройку hosts следующим образом:

```
hosts:         files dns wins
```

Всё, теперь к клиентам можно обращаться через hostname, даже через Windows.

Статья по настройке hostname лежит [здесь](https://goldarte.gitbooks.io/dev_notes/content/nastroika-hostname-na-svyazke-rpi+cleverros.html).

