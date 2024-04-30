tce-load -wi squashfs-tools fontconfig

mkdir -p pkg/usr/local/share/fonts

cp -R /mnt/sdc/cyrillic pkg/usr/local/share/fonts

mkdir -p pkg/usr/tce.installed

echo -e "#!/bin/sh\n\nfc-cache /usr/local/share/fonts/cyrillic" > pkg/usr/tce.installed/cyrillic-fonts

mksquashfs pkg cyrillic-fonts.tcz

cp cyrillic-fonts.tcz /etc/sysconfig/tcedir/optional/

echo cyrillic-fonts.tcz >> /etc/sysconfig/tcedir/onboot.lst

echo "fontconfig.tcz" > /etc/sysconfig/tcedir/optional/cyrillic-fonts.tcz.dep
