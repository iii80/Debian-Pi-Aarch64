
#### 再次重申！我们是团队，企业级团队出品的系统，不要拿个人作品来和我们比较。

![openfans](../images/openfans.png)&nbsp;&nbsp;&nbsp;&nbsp;![amatfan.png](../images/amatfan.png)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[OPENFANS开源社区](http://www.openfans.org)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[树莓派爱好者基地](http://rpifans.cn/)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**荣誉出品 ！！**

----

#### Disable cgroup

In cmdline.txt remove defined cgoup args and add:

```shell
cgroup_disable=cpuset,cpuacct,blkio,memory,devices,freezer,net_cls,perf_event,net_prio,pids
```

#### ssh glxinfo

```shell
export DISPLAY=:0
export XAUTHORITY=/var/lib/lightdm/.Xauthority
glxinfo -B
```

#### initrd

```shell
apt update ; apt install initramfs-tools -y
mkinitramfs -o /boot/initrd.img-$(uname -r)
      
#### /var/log/Xorg.0.log

```shell
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
sudo apt install xfonts-cyrillic
```

#### chromium

```shell
rm -rf /usr/sbin/chromium_mod-xface.sh 2>/dev/null;\
cat <<EOF >/usr/sbin/chromium_mod-xface.sh
#!/bin/bash
export PICHROMIUMMODS='/etc/chromium.d/pi-mods'
touch \$PICHROMIUMMODS 2>/dev/null
echo 'CHROMIUM_FLAGS=' > \$PICHROMIUMMODS
sed -i 's/CHROMIUM_FLAGS=/CHROMIUM_FLAGS="\$CHROMIUM_FLAGS --disable-gpu-compositing --enable-gpu-rasterization --enable-native-gpu-memory-buffers --disable-quic --enable-checker-imaging --enable-tcp-fast-open--enable-fast-unload --enable-experimental-canvas-features --enable-scroll-prediction --enable-simple-cache-backend --answers-in-suggest --max-tiles-for-interest-area=512 --num-raster-threads=4 --default-tile-height=512 --disk-cache-size=0 --use-gl=egl --gles --enable-zero-copy"/g' \$PICHROMIUMMODS
EOF
sudo chmod +x /usr/sbin/chromium_mod-xface.sh

## --disable-gpu-compositing to use vc4 ??
```

#### libGL.so armhf

```shell
apt install libgl1-mesa-dri:armhf libgl1-mesa-glx:armhf glx-alternative-mesa:armhf
```
