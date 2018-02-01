#### Статья

[https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh](https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh)

#### Кратко

Примонтировать SSH:

```
sshfs -o allow_other,default_permissions,IdentityFile=~/.ssh/id_rsa root@192.168.11.1:/ ~/coex_ssh
```

Размонтировать:

```
sudo fusermount -uz ~/coex_ssh
```



