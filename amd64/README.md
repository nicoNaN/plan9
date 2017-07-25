# Building & installing amd64 kernel on 9front

```
% cd /
% rc /sys/lib/rootstub
% cd /sys/src
% objtype=amd64 mk install
% cd /sys/src/9/pc64
% mk install
```

Now the amd64 kernel has been built. Before copying it to 9bootfat so we can boot from it, do

```
% 9fs 9fat
% rm /n/9fat/9bootfat
% cp /386/9bootfat /n/9fat/ # I think bootloader is 386 only, so do this even when installing amd64
% chmod +al /n/9fat/9bootfat # defrag magic
```

Next, copy the kernel

```
% cp /amd64/9pc64 /n/9fat/
```

Finally, edit the `bootfile` variable in `plan9.ini` to use the `9pc64` kernel: `bootfile=9pc64`

Reboot.
