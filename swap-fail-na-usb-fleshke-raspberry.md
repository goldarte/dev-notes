Как монтировать usb диск на raspberry:

Основная статья: [https://www.htpcguides.com/properly-mount-usb-storage-raspberry-pi/](https://www.htpcguides.com/properly-mount-usb-storage-raspberry-pi/)

```
First make a directory in which to mount the USB drive

sudo mkdir /mnt/usbstorage

Make pi the owner of the mounted drive and make its permissions read, write and execute for it

sudo chown -R pi:pi /mnt/usbstorage
sudo chmod -R 775 /mnt/usbstorage

Set all future permissions for the mount point to pi user and group (explanation can be found here)

sudo setfacl -Rdm g:pi:rwx /mnt/usbstorage
sudo setfacl -Rm g:pi:rwx /mnt/usbstorage

For all drive types mount the usb with this command, -o insures pi is the owner which should avoid permission issues

sudo mount -o uid=pi,gid=pi /dev/sda1 /mnt/usbstorage
```

Как редактировать конфигурацию swap файла:

Основная статья: [https://raspberrypi.stackexchange.com/questions/70/how-to-set-up-swap-space](https://raspberrypi.stackexchange.com/questions/70/how-to-set-up-swap-space)

```
The configuration file is:

/etc/dphys-swapfile 

The content is very simple. By default my Raspbian has 100MB of swap:

CONF_SWAPSIZE=100

If you want to change the size, you need to modify the number and restart dphys-swapfile:

/etc/init.d/dphys-swapfile stop
/etc/init.d/dphys-swapfile start

Edit: On Raspbian the default location is /var/swap, which is (of course) located on the SD card. I think it is a bad idea, so I would like to point out, that the /etc/dphys-swapfile can have the following option too: CONF_SWAPFILE=/media/btsync/swapfile
```



